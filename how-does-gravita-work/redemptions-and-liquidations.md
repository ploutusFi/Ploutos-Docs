# Redemptions and Liquidations

## What are the differences between Redemptions and Liquidations?

Redemption is a mechanism that makes a user reduce exposure to the collateral of their choice in the specific vessel that is redeemed.\
\
Liquidation happens when a Vessel is fully closed after it goes above the maximum LTV required by the protocol, forcing the user to lose the entire balance of collateral. However, after a liquidation happens, the user does not need anymore to pay back their debt.

It is important to note that bLUSD Vessels cannot be liquidated or redeemed against. Liquidations and redemptions against bLUSD are not possible at a protocol level. As we work towards improving the bLUSD price feed (currently fixed at $ 1 USD), we care about iterating that bLUSD in Levra Protocol is exempt from liquidations, redemptions and recovery mode.

## Redemptions

Redemptions allow USDL holders to directly redeem their USDL for collateral from the vessels with the hiughest LTV in the system. This mechanism ensures that USDL maintains a price close to the redemption parameter.

### What are redemptions?

The redemption mechanism gives USDL holders the ability to redeem USDL for a certain amount of USD-worth of underlying collateral at any time. \
\
The redemptions timeline is the following:\
\
\- Launch: Redemptions are disabled\
\- 18th of July 2023: 0.98\
\- 18th of August 2023: 0.99\
\- 18th of September 2023: 0.995\
\- 18th of October 2023: 1\
\- 06th of November 2023: 0.9975 on Mainnet, 0.995 on Arbitrum and other L2s

This means that there is a 1-(current redemption parameter) fee in place for redemptions that is paid out to the borrower you are redeeming against, on top of a redemption fee that is paid out to the protocol. \
\
It will not initially possible to redeem collateral against other users through our web interface.

Redemptions happen first to the Vessel with the highest LTV. It is important to note that, in some environments, even LTVs at 40% or below cannot be considered "safe" against redemptions, if you are the user with the highest LTV. In order to avoid redemptions, a user needs to keep a low LTV compared to the one of the other participants in the protocol. Alternatively, USDL price needs to regularly trade above the redemption parameter. During such circumstances, your risk of being redeemed against decreases. \
\
When you launch your Vessel, you can always see through our UI how much USDL needs to be redeemed for your collateral to start being impacted, at the mention "Debt ahead".

### Is a redemption the same as paying back my debt?&#x20;

No, redemptions are a completely separate mechanism. All one has to do to pay back their debt is adjust their Vessel's debt and collateral.&#x20;

### As a borrower, do I lose money if I'm redeemed against?&#x20;

If your Vessel is redeemed against, you _do not_ incur a net loss. However, you will lose exposure to the collateral of your choice. Your Vessel's LTV will also improve after a redemption, or your Vessel will be fully closed.

### How can I avoid being redeemed against?&#x20;

The best way to avoid being redeemed against is by maintaining a low LTV relative to the rest of the Vessels in the system. A "Debt Ahead" value is displayed when launching a Vessel, indicating how much USDL needs to be redeemed before your Vessel is affected. Remember: The riskiest Vessels (i.e. lowest collateralized Vessels) are first in line when a redemption takes place.&#x20;

### How It Works

Redemptions can currently only be performed by bots or by interacting direclty with our smart contracts.

1. **Initiation**: A USDL holder (typically a bot) initiates a redemption by sending USDL to the Levra smart contract and indicating the amount they wish to redeem.
2. **Execution**: The protocol automatically identifies the vessels with the highest LTV collateral ratios (starting from the highest and moving downwards) and redeems the USDL for collateral (based on the oracle price) from these vessels. The collateral is then sent to the redeemer's address with a small fee that is collected by the protocol.
3. **Impact on Vessels**: The redeemed USDL is burned, and the corresponding amount of collateral is removed from the collateral of the affected vessels. This process continues until the total amount of USDL requested for redemption has been fulfilled.

### Stability Mechanism

The redemption mechanism is a crucial stabilizer for USDL. In scenarios where USDL trades below its redemption parameter, users are incentivized to buy USDL at a discount and redeem it for collateral with a superior value, thus reducing the USDL supply and helping it trade closer to its redemption parameter. Conversely, when USDL is above the redemption parameter, users are incentivized to launch vessels (borrow USDL) and sell it for a profit, increasing USDL supply until the peg is restored.

## Liquidations

### What are liquidations?

To ensure that the entire USDL supply remains fully backed by collateral, Vessels that go above the maximum LTV[ defined in this page](vessels-and-collateral.md) will be closed (liquidated).

The debt of the Vessel is cancelled and absorbed by the [Stability Pool](stability-pool.md) and its collateral distributed among Stability Providers.

The owner of the Vessel still keeps the full amount of USDL borrowed and will not need to repay their debt.

[System Status](system-status-and-price-volatility.md) affects how Liquidations work. Make sure to understand well Recovery Mode to avoid an unexpected liquidation.

### Who can liquidate Vessels?&#x20;

Anybody can liquidate a Vessel as soon as it goes above the maximum LTV. The initiator receives a gas compensation (`200 USDL`), plus `0.5%` of the Vessel's collateral as reward for this service.
