# Levra Protocol Documentation

> ⚠️ **Levra is a 100% fork of [Gravita Protocol](https://docs.gravitaprotocol.com/).**
>
> The only changes introduced are:
> - The DebtToken symbol (**GRAI → USDL**)
> - The DebtToken name (**Levra Debt Token**)
>
> All other mechanics, smart contracts, and architecture remain fully identical to the original Gravita Protocol.

# Overview

**Please review our Disclaimer and Terms of Service before using the Levra Protocol or interacting with USDL.**

Levra Protocol is a decentralised borrowing protocol built on Ethereum that provides users with interest-free loans secured by both Liquid Staking Tokens (LST) and a Stability Pool (SP).\
\
Loans are issued in the form of minting **USDL**, a token with similar volatility dampening mechanism as LUSD, and can be _up to_ 90% of the value of a user's collateral (99% in the case of bLUSD).&#x20;

You can find more information on the maximum LTV ratio of the supported assets in our [Vessels and Collateral page.](how-does-gravita-work/vessels-and-collateral.md)\
\
Levra Protocol builds off [Liquity's economic model](https://github.com/liquity/dev) to ensure efficient borrowing and timely liquidations. A one-off borrowing fee is charged upfront on each new debt (or debt increase). In order to incentivize short-term borrowing, the fee is refunded if the user repays his debt before the expiry of six months (\~182 days), pro rata for the time elapsed, but the minimum fee corresponds to one week worth of interest. You will find more information on the [Fee Model](how-does-gravita-work/fee-model.md) page.\
\
Levra has an unique multi-collateral design in which each position has a single collateral type, but they are all linked to the same stability pool:&#x20;

<figure><img src=".gitbook/assets/multi-collateral.png" alt=""><figcaption></figcaption></figure>

Borrowers mint USDL against the value of their collateral. It can then be used in various ways - swapping for other assets, or earning income by providing liquidity or participating in the stability pool.\
\
In order to reduce the volatility of USDL, a Liquity-like redemption mechanism is enabled. \
\
Levra Protocol is non-custodial, with the goal of becoming more ossified and governance-minimised.


## Attribution / Credits

Levra is based entirely on the open-source work of the **[Gravita Protocol](https://docs.gravitaprotocol.com/)** team.  
We acknowledge and thank the Gravita contributors for their development, documentation, and research efforts that made this fork possible.