---
description: >-
  This page explains the contract changes that were implemented within the yield
  farming contract aka the "MasterFarmer" contract
---

# Contract Changes

Many are familiar with yield farming protocols including Yam, Sushi and Lua.

Many may expect that Bao follows the same exact patterns of these systems.\
\
For transparency, we wanted to outline some key changes that this system has.

## Authorization Module

```
contract Authorizable is Ownable {

    mapping(address => bool) public authorized;

    modifier onlyAuthorized() {
        require(authorized[msg.sender] || owner() == msg.sender);
        _;
    }

    function addAuthorized(address _toAdd) onlyOwner public {
        authorized[_toAdd] = true;
    }

    function removeAuthorized(address _toRemove) onlyOwner public {
        require(_toRemove != msg.sender);
        authorized[_toRemove] = false;
    }

}
```

The authorization module is an extension of the ownable module standard for ERC-20 contracts.\
\
This allows us to create a list of approved wallets that can use specific commands as if they were an owner. We did this because the BaoMasterFarmer contract must be an owner of the Bao Token contract, but in the future, we will wish to migrate this to new contracts such as synthetic asset contracts.

The authorization module is used only in reclaiming ownership and minting the initial issuance of tokens for seeding the ecosystem.

## Timelocker Module

Similar to the Authorization Module extension, we have created a "Timelocker" status as well.

The Timelocker status locks the migration (and only the migration) so that it will always need to go through the timelock contract.

## Locking System

Unlike Sushi distributions, we also add the concept of "Locking". When a user earns the bao token, 95% of it is locked up and distributed to them over a 3-year time period and only 5% can be harvested and available immediately.\
\
The dev fund and founders fund have these same lockups.

The lockups do not begin to release until after 1-year, and they unlock linearly, with every block over the 3 years.\
\
This means that while users earn their bao early, they will vest their tokens over time just like the teams do, in order to create harmonious users who are aligned with the community goals.

Because the lock of the token is part of the bao token natively, this means once a user earns it, the Bao Team can **not** retrieve the tokens from the user. It is in their possession even if it is locked. They will be able to claim and use the token once the timelock expires.

```
 function canUnlockAmount(address _holder) public view returns (uint256) {
        if (block.number < lockFromBlock) {
            return 0;
        }
        else if (block.number >= lockToBlock) {
            return _locks[_holder];
        }
        else {
            uint256 releaseBlock = block.number.sub(_lastUnlockBlock[_holder]);
            uint256 numberLockBlock = lockToBlock.sub(_lastUnlockBlock[_holder]);
            return _locks[_holder].mul(releaseBlock).div(numberLockBlock);
        }
    }

    function unlock() public {
        require(_locks[msg.sender] > 0, "ERC20: cannot unlock");
        
        uint256 amount = canUnlockAmount(msg.sender);
        // just for sure
        if (amount > balanceOf(address(this))) {
            amount = balanceOf(address(this));
        }
        _transfer(address(this), msg.sender, amount);
        _locks[msg.sender] = _locks[msg.sender].sub(amount);
        _lastUnlockBlock[msg.sender] = block.number;
        _totalLock = _totalLock.sub(amount);
    }

    // This function is for dev address migrate all balance to a multi sig address
    function transferAll(address _to) public {
        _locks[_to] = _locks[_to].add(_locks[msg.sender]);

        if (_lastUnlockBlock[_to] < lockFromBlock) {
            _lastUnlockBlock[_to] = lockFromBlock;
        }

        if (_lastUnlockBlock[_to] < _lastUnlockBlock[msg.sender]) {
            _lastUnlockBlock[_to] = _lastUnlockBlock[msg.sender];
        }

        _locks[msg.sender] = 0;
        _lastUnlockBlock[msg.sender] = 0;

        _transfer(msg.sender, _to, balanceOf(msg.sender));
    }
```

## Block Deltas and Fee/Penalty System

As part of each user object, we now include tracking of deposit and withdrawal blocks.\
\
This is to allow us to track the time between deposits and withdrawals. We use this for our fee and penalty system that discourages short term users from rapidly leaving the system

```
// Info of each user.
struct UserInfo {
    uint256 amount;     // How many LP tokens the user has provided.
    uint256 rewardDebt; // Reward debt. See explanation below.
    uint256 rewardDebtAtBlock; // the last block user stake
    uint256 lastWithdrawBlock; // the last block a user withdrew at.
    uint256 firstDepositBlock; // the last block a user deposited at.
    uint256 blockdelta; //time passed since withdrawals
    uint256 lastDepositBlock;
```

When users make a withdrawal, we check how long they have been in the pool and apply a small fee or a large penalty depending on the behavior. For example a fee of 0.25% is taken if the user was in the pool for more than 2 weeks but less than 4 weeks, but if the user tries to do a flash loan exploit and leave in the same block they have entered then we apply 25% penalty for discouragement.



```
if(user.blockdelta == 0 || block.number == user.lastDepositBlock){
				//25% fee for withdrawals of LP tokens in the same block this is to prevent abuse from flashloans
				pool.lpToken.safeTransfer(address(msg.sender), _amount.mul(75).div(100));
				pool.lpToken.safeTransfer(address(devaddr), _amount.mul(25).div(100));
			} else if (user.blockdelta > 0 && user.blockdelta <= 274){
				//8% fee if a user deposits and withdraws in under between same block and 59 minutes.
				pool.lpToken.safeTransfer(address(msg.sender), _amount.mul(92).div(100));
				pool.lpToken.safeTransfer(address(devaddr), _amount.mul(8).div(100));
			} else if (user.blockdelta >= 275 && user.blockdelta <= 6600){
				//4% fee if a user deposits and withdraws after 1 hour but before 1 day.
				pool.lpToken.safeTransfer(address(msg.sender), _amount.mul(96).div(100));
				pool.lpToken.safeTransfer(address(devaddr), _amount.mul(4).div(100));
			} else if (user.blockdelta >= 6601 && user.blockdelta <= 19800){
				//2% fee if a user deposits and withdraws between after 1 day but before 3 days.
				pool.lpToken.safeTransfer(address(msg.sender), _amount.mul(98).div(100));
				pool.lpToken.safeTransfer(address(devaddr), _amount.mul(2).div(100));
			} else if (user.blockdelta >= 19441 && user.blockdelta <= 33000){
				//1% fee if a user deposits and withdraws after 3 days but before 5 days.
				pool.lpToken.safeTransfer(address(msg.sender), _amount.mul(99).div(100));
				pool.lpToken.safeTransfer(address(devaddr), _amount.mul(1).div(100));
			}  else if (user.blockdelta >= 33001 && user.blockdelta <= 90720){
				//0.5% fee if a user deposits and withdraws if the user withdraws after 5 days but before 2 weeks.
				pool.lpToken.safeTransfer(address(msg.sender), _amount.mul(995).div(1000));
				pool.lpToken.safeTransfer(address(devaddr), _amount.mul(5).div(1000));
			} else if (user.blockdelta >= 90721 && user.blockdelta <= 181440){
				//0.25% fee if a user deposits and withdraws after 2 weeks.
				pool.lpToken.safeTransfer(address(msg.sender), _amount.mul(9975).div(10000));
				pool.lpToken.safeTransfer(address(devaddr), _amount.mul(25).div(10000));
			} else if (user.blockdelta > 181441) {
				//0.1% fee if a user deposits and withdraws after 4 weeks.
				pool.lpToken.safeTransfer(address(msg.sender), _amount.mul(9999).div(10000));
				pool.lpToken.safeTransfer(address(devaddr), _amount.mul(1).div(10000));
			}
```

## Revision Functions:

Since tracking block delta is experimental, and there may be other issues around fee tracking the owner has two commands to manually update the user deposit and withdraw numbers in case of emergency:

```
function reviseWithdraw(uint _pid, address _user, uint256 _block) public onlyOwner {
   UserInfo storage user = userInfo[_pid][_user];
   user.lastWithdrawBlock = _block;

}

function reviseDeposit(uint _pid, address _user, uint256 _block) public onlyOwner {
   UserInfo storage user = userInfo[_pid][_user];
   user.firstDepositBlock = _block;

}
```

## Manual Mint

The authorized owner of the Bao Token contract has a specific command for manual minting the initial allocation of Bao. This allows them to only create up to the approved cap and then never mint again:

```
function manualMint(address _to, uint256 _amount) public onlyAuthorized {
    if(manualMinted < manualMintLimit){
        _mint(_to, _amount);
        _moveDelegates(address(0), _delegates[_to], _amount);
        manualMinted = manualMinted + _amount;
    }
}
```

## Reclaim Owner

Since the Bao Token contract needs to be owned by the BaoMasterFarmer contract we have added a function for reclaiming ownership back to the deployer address:

```
function reclaimOwnership(address newOwner) public virtual onlyPreviousOwner {
    require(newOwner == _previousOwner, "Ownable: new owner must be previous owner");
    emit OwnershipTransferred(_owner, newOwner);
    _owner = newOwner;
}
```
