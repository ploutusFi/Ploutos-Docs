# Redemptions and Liquidations

## What are the differences between Redemptions and Liquidations?

Redemption is a mechanism that makes a user reduce exposure to the collateral of their choice in the specific vessel that is redeemed.\
\
Liquidation happens when a Vessel is fully closed after it goes above the maximum LTV required by the protocol, forcing the user to lose the entire balance of collateral. However, after a liquidation happens, the user does not need anymore to pay back their debt.

It is important to note that bLUSD Vessels cannot be liquidated or redeemed against. Liquidations and redemptions against bLUSD are not possible at a protocol level. As we work towards improving the bLUSD price feed (currently fixed at $ 1 USD), we care about iterating that bLUSD in Gravita Protocol is exempt from liquidations, redemptions and recovery mode.

## Redemptions

### What are redemptions?

The redemption mechanism gives GRAI holders the ability to redeem GRAI for a certain amount of USD worth of underlying collateral at any time. \
\
The redemptions timeline is the following:\
\
\- Launch: Redemptions are disabled\
\- 18th of July 2023: 0.98\
\- 18th of August 2023: 0.99\
\- 18th of September 2023: 0.995\
\- 18th of October 2023: 1

This means that there is a 1-(current redemption parameter) fee in place for redemptions that is paid out to the borrower you are redeeming against, on top of a redemption fee that is paid out to the protocol. \
\
It will not initially possible to redeem collateral against other users through our web interface.

Only the riskiest Vessels are redeemed against: if you keep a low LTV, your risk of being redeemed against decreases. Once you open a Vessel, you can always see through our UI how much GRAI needs to be redeemed for your collateral to start being impacted, at the mention "Debt ahead".

### Is a redemption the same as paying back my debt?&#x20;

No, redemptions are a completely separate mechanism. All one has to do to pay back their debt is adjust their Vessel's debt and collateral.&#x20;

### As a borrower, do I lose money if I'm redeemed against?&#x20;

If your Vessel is redeemed against, you _do not_ incur a net loss. However, you will lose some of your collateral exposure. Your Vessel's LTV will also improve after a redemption.&#x20;

### How can I avoid being redeemed against?&#x20;

The best way to avoid being redeemed against is by maintaining a low LTV relative to the rest of the Vessels in the system. Remember: The riskiest Vessels (i.e. lowest collateralized Vessels) are first in line when a redemption takes place.&#x20;

## Liquidations

### What are liquidations?

To ensure that the entire GRAI supply remains fully backed by collateral, Vessels that go above the maximum LTV[ defined in this page](vessels-and-collateral.md) will be closed (liquidated).

The debt of the Vessel is cancelled and absorbed by the [Stability Pool](stability-pool.md) and its collateral distributed among Stability Providers.

The owner of the Vessel still keeps the full amount of GRAI borrowed and will not need to repay their debt.

[System Status](system-status-and-price-volatility.md) affects how Liquidations work. Make sure to understand well Recovery Mode to avoid an unexpected liquidation.

### Who can liquidate Vessels?&#x20;

Anybody can liquidate a Vessel as soon as it goes above the maximum LTV. The initiator receives a gas compensation (`200 GRAI`), plus `0.5%` of the Vessel's collateral as reward for this service.
