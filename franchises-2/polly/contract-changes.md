# Contract changes

## NestContracts

All contracts are forked from the PieDao deployment on the Ethereum Mainnet, with some minor changes that allow them to function on Polygon.\
\
These changes are detailed below.\
\
In order to understand the smart contract setup and query the nests correctly, you will have to familiarize yourself with the _Diamond Standard_ architecture, with which these contracts were built [https://eips.ethereum.org/EIPS/eip-2535](https://eips.ethereum.org/EIPS/eip-2535).

## Contract Changes

The original contracts deployed by PieDao can be found here:\
[https://docs.piedao.org/technical/deployed-smart-contracts](https://docs.piedao.org/technical/deployed-smart-contracts)\
\
The contracts were ported as-is from the PieDaos implementation on Main net with a few exceptions: On the Polygon network, the Aave protocol requires the sender to state the address where the amTokens or underlying tokens should be sent when depositing or withdrawing. This required small changes in the following contracts:\
\
**ILendingLogic.sol**

```
	function lend(address _underlying, uint256 _amount, address _tokenHolder) external view returns(address[] memory targets, bytes[] memory data);

	function unlend(address _wrapped, uint256 _amount, address _tokenHolder) external view returns(address[] memory targets, bytes[] memory data);
```

**LendingRegestry.sol**

```
function getLendTXData(address _underlying, uint256 _amount, address _tokenHolder, bytes32 _protocol) external view returns(address[] memory targets, bytes[] memory data) {
	ILendingLogic lendingLogic = ILendingLogic(protocolToLogic[_protocol]);
	require(address(lendingLogic) != address(0), "NO_LENDING_LOGIC_SET");

	return lendingLogic.lend(_underlying, _amount, _tokenHolder);
}
```

**AaveLendingLogic.sol**

```
function lend(address _underlying,uint256 _amount, address _tokenHolder) external view override returns(address[] memory targets, bytes[] memory data) {
[...]
data[2] =  abi.encodeWithSelector(lendingPool.deposit.selector, _underlying, _amount, _tokenHolder, referralCode);
}

function unlend(address _wrapped, uint256 _amount,address _tokenHolder) external view override returns(address[] memory targets, bytes[] memory data) {
[...]
data[0] = abi.encodeWithSelector(
	lendingPool.withdraw.selector,
	wrapped.UNDERLYING_ASSET_ADDRESS(),
	_amount,
	_tokenHolder
);
}
```

**CREAMLendingLogic.sol**

```
function lend(address _underlying, uint256 _amount, address _tokenHolder) external view override returns(address[] memory targets, bytes[] memory data) {
}

function unlend(address _wrapped, uint256 _amount, address _tokenHolder) external view override returns(address[] memory targets, bytes[] memory data) {
}
```

The contracts listed above do not have any access to the funds that are held by the nest. Worst case scenario, errors in these contracts would result in the user minting a wrong amount of a nest or the user would fail to mint the nest.

**LendingManger.sol**

Changing the LendingManager requires increased vigilance, as it has direct access to the Nests funds. This is the only change made to the LendingManager:

BEFORE CHANGE

```
) = lendingRegistry.getLendTXData(_underlying, amount, _protocol);
```

AFTER CHANGE

```
) = lendingRegistry.getLendTXData(_underlying, amount, address(basket),_protocol);
```

The `basket` constant is set on deployment and cannot be changed retroactively.

```
constructor(address _lendingRegistry, address _basket) public {
require(_lendingRegistry != address(0), "INVALID_LENDING_REGISTRY");
require(_basket != address(0), "INVALID_BASKET");
lendingRegistry = LendingRegistry(_lendingRegistry);
basket = IExperiPie(_basket);
}
```

The basket address is the address of the nest that the LendingManager is assigned to.

The "Recipe" contract is used to swap the user's wETH for the index assets and lend them in a specific protocol when needed. As the recipe does not have access to any funds deposited in the index, we felt like more liberties could be made adjusting the code. The following is a change that allows us to take an entry fee that is exchanged for Polly and then burned:

```
if(remainingInputBalance > 0 && feeAmount != 0) {
	WETH.approve(address(sushiRouter), 0);
	WETH.approve(address(sushiRouter), type(uint256).max);
	address[] memory route = getRoute(address(WETH), baoAddress);
	uint256 estimatedAmount = sushiRouter.getAmountsOut(feeAmount, route)[1];
	sushiRouter.swapExactTokensForTokens(feeAmount, estimatedAmount, route, address(this), block.timestamp + 1);
	baoToken.burn(baoToken.balanceOf(address(this)));    
}
```

Originally the recipe always looks at Uniswap and SushiSwap to identify the best price. The new Recipe does not check the prices and only trades on SushiSwap.

```
function getBestPriceSushiUni(address _inputToken, address _outputToken, uint256 _outputAmount) internal returns(uint256, DexChoice) {
	uint256 sushiAmount = getPriceUniLike(_inputToken, _outputToken, _outputAmount, sushiRouter);

	return (sushiAmount, DexChoice.Sushi);
}
```

## Changes difference

Fabiaz from the Quality Assurance Galaxy put a detailed comparison between the two versions of the code here: [Fabiaz diff comparaison on GitHub](https://github.com/fabiaz84/Polly-Contracts/commit/4e222df69a04c04c0b7b298e8e005704a58c0541)
