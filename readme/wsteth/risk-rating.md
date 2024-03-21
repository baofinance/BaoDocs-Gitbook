# Risk Rating

## Risk Rating <a href="#id-614-risk-rating" id="id-614-risk-rating"></a>

Based on the risks identified for each category, the following chart summarizes a risk rating for wstETH as collateral. The rating for each category is ranked from excellent, good, ok, and poor.

* We rank wstETH **excellent on liquidity** for being the clear market leader with deepest liquidity.
* We rank wstETH **ok in volatility** due to multiple depeg events pre-Shanghai and a high level of uncertainty about withdrawal processing, which may inhibit arbitrage.
* We rank wstETH **good in smart contracts** for being heavily audited, having a bug bounty program, and having a long history securing billions in TVL without major incident. The recent upgrade to V2 increases smart contract uncertainty.
* We rank wstETH **ok in dependencies** for having a reliable pricefeed available. Dependency of lido oracle daemons can result in disruptions that can cause incorrect reward distribution or liquidity mismanagement. Execution Layer clients are dominated by Go-Ethereum (Geth), which could lead to invalid blocks being validated and being locked into an invalid finalized chain, all but guaranteeing the majority of staked ETH are burned. Lido recognise this risk and are making changes to ensure a more diverse range of execution layer clients.
* We rank wstETH **good in centralization** for having core system controls with a DAO that has reasonable backstop measures. Multiple multisigs are employed with limited privileges for specific precautionary functions.
* We rank wstETH **good in legal** for having no enforcement actions historically, Lido limits liability in their terms and conditions and decentralization is sufficient that legal action is unlikely to disrupt the network. A concentration of NOs in Europe increases vulnerability in those jurisdictions.

The overall risk profile and persistently dominant market standing of Lido make wstETH suitable as a core collateral type within Bao Finance. All additional LSDs reviewed will undergo a comparative analysis against Lido to determine how well they complement wstETH for suitability within the collateral basket.
