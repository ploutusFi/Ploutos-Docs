# Overview

**Please review our Disclaimer and Terms of Service before using the Gravita Protocol or interacting with GRAI.**

Gravita Protocol is a decentralised borrowing protocol built on Ethereum that provides users with interest-free loans secured by both Liquid Staking Tokens (LST) and a Stability Pool (SP).\
\
Loans are issued in the form of minting **GRAI**, a token with similar volatility dampening mechanism as LUSD, and can be _up to_ 90% of the value of a user's collateral (99% in the case of bLUSD).&#x20;

You can find more information on the maximum LTV ratio of the supported assets in our [Vessels and Collateral page.](how-does-gravita-work/vessels-and-collateral.md)\
\
Gravita Protocol builds off [Liquity's economic model](https://github.com/liquity/dev) to ensure efficient borrowing and timely liquidations. A standard 0,5% borrowing fee is charged upfront on each new debt (or debt increase). In order to incentivize short-term borrowing, the fee is refunded if the user repays his debt before the expiry of six months (\~182 days), pro rata for the time elapsed, but the minimum fee corresponds to one week worth of interest. You will find more information on the [Fee Model](how-does-gravita-work/fee-model.md) page.\
\
Gravita has an unique multi-collateral design in which each position has a single collateral type, but they are all linked to the same stability pool:&#x20;

<figure><img src=".gitbook/assets/multi-collateral.png" alt=""><figcaption></figcaption></figure>

Borrowers mint GRAI against the value of their collateral. It can then be used in various ways - swapping for other assets, or earning income by providing liquidity or participating in the stability pool.\
\
In order to reduce the volatility of GRAI, a Liquity-like redemption mechanism will be enabled after launch. Redemptions are made at a rate of 0.97 to 1 (the redeemer pays a 3% fee to the borrower).\
\
Gravita Protocol is non-custodial and governance-minimised, with the goal of becoming immutable.
