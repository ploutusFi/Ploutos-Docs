# System Status and Price Volatility

## System Status

Levra Protocol displays on its front-end a System Status. The value displayed is based on the current system LTV.&#x20;

<mark style="color:green;">Normal</mark> is displayed when the LTV of a specific collateral type is healthy.

<mark style="color:yellow;">Caution</mark> is displayed when the LTV of a specific collateral type is approaching the Maximum System LTV.&#x20;

<mark style="color:red;">Recovery mode</mark> is displayed when the LTV of a specific collateral type is greater than the Maximum System LTV.

On Levra Protocol, despite the existence of a common Stability Pool, **each collateral type has an independent System Status.** As a consequence, a specific collateral type can be in Recovery Mode while others aren't.&#x20;

| Token  | Critical Collateral Ratio (CCR) | Maximum System LTV |
|--------|---------------------------------|--------------------|
| WETH   | 1.4                             | 71%                |
| sAVAX  | 1.5                             | 66%                |
| WETH.e | 1.5                             | 66%                |
| GHO    | 1.3                             | 77%                |
| USDC   | 1.2                             | 83%                |
| USDT   | 1.2                             | 83%                |
| AUSD   | 1.5                             | 66%                |

<mark style="color:yellow;">**In order to better give users an understanding of how Levra Protocol works, the following examples will be only be made using WETH as a collateral type.**</mark>

### What is Recovery mode?&#x20;

Recovery Mode kicks in when the total LTV of one specific collateral type in Levra Protocol goes  **above the maximum LTV.**

_**During Recovery Mode, Vessels with an LTV of 71.4% or more can be liquidated.**_&#x20;

Even though further in this page we are taking as an example only WETH vessel, it is true for all collateral types (except bLUSD) that during Recovery Mode Vessels with an LTV of 71.4% or more can be liquidated.&#x20;

Moreover, the system blocks borrower transactions that would further increase the LTV. New USDL may only be issued by opening a new Vessel with an LTV below 71.4%.

The goal of Recovery Mode is to incentivize borrowers to behave in ways that promptly reduce the LTV back below the Maximum System LTV and to incentivize USDL holders to replenish the Stability Pool.

Economically, Recovery Mode is designed to encourage collateral top-ups and debt repayments, and also itself acts as a self-negating deterrent: the possibility of it occurring actually guides the system away from ever reaching it. Recovery Mode is not a desirable state for the system.&#x20;

### How can I make my Vessel safe in Recovery Mode?

By lowering your LTV to 71.4% or less. You can do this by adding collateral or repaying part of your debt in USDL.

### How do liquidations work?&#x20;

In Normal Mode Liquidations can only happen if your LTV goes above the Maximum LTV described [on this page.\
](vessels-and-collateral.md)\
In recovery mode, the following parameters affect the behaviour of Levra Protocol during recovery mode:

* ILTV = Individual Loan-to-Value Ratio&#x20;
* MLTV = Maximum Loan-to-Value Ratio
* TLTV = current Total Loan-to-Value Ratio&#x20;
* SP USDL = Amount of USDL in the Stability Pool
* Vessel Debt = The amount of USDL taken as a loan from a Vessel

<table data-header-hidden><thead><tr><th width="322">Condition                                              </th><th>Liquidation Behavior</th></tr></thead><tbody><tr><td>Condition                                              </td><td>Liquidation Behaviour</td></tr><tr><td>ILTV >=100%</td><td>Redistribute all debt and collateral (minus compensation) to active Vessels of the same collateral type.</td></tr><tr><td>MLTV &#x3C; ILTV &#x3C; 100% &#x26; SP USDL > Vessel debt</td><td>USDL in the Stability Pool equal to the Vessel's debt is <em>offset</em> with the Vessel's debt. The Vessel's collateral (minus the liquidator compensation) is shared between depositors.</td></tr><tr><td>MLTV &#x3C; ILTV &#x3C; 100% &#x26; SP USDL &#x3C; Vessel debt</td><td>The total Stability Pool USDL is offset with an equal amount of debt from the Vessel. A fraction of the Vessel's collateral (equal to the ratio of its offset debt to its entire debt) is shared between Stability Providers. The remaining debt and collateral (minus the liquidator compensation) is redistributed to active Vessels to reduce their TVL.</td></tr><tr><td>TLTV &#x3C; ILTV &#x3C;= MLTV &#x26; SP USDL >= Vessel debt</td><td>The Stability Pool USDL is offset with an equal amount of debt from the Vessel. A fraction of collateral with dollar value equal to <code>1.1 * debt</code> for WETH is shared between Stability Providers. Nothing is redistributed to other active Vessels. Since its ILTV was <code>&#x3C; 0.90</code>, the Vessel has a collateral remainder, which is sent to the <code>CollSurplusPool</code> and is claimable by the borrower. The Vessel is closed.</td></tr><tr><td>TLTV &#x3C; ILTV &#x3C;= MLTV  &#x26; SP USDL &#x3C; Vessel debt</td><td>Do nothing.</td></tr><tr><td>ILTV &#x3C;= TLTV</td><td>Do nothing.</td></tr></tbody></table>

A good rule of thumb is to be under the TLTV and the MLTV in recovery mode. it is advisable to also monitor the TLTV to avoid liquidation.\
\
For Vessels opened with bLUSD as collateral, Levra Protocol did not implement a Liquidation or Redemption mechanism. This means that Stability Providers will not capture any bLUSD, since it cannot be liquidated or redeemed against.\
\
It is important to note that, because of it's design, actions taken by users interacting with the Smart Contracts developed by Levra Protocol will _always_ value 1 USDL as if it is worth $ 1 USD.&#x20;

This does not mean that the value of USDL will always be equal to $ 1 USD; users need to be aware that the price of USDL can and will very likely move below or above those ranges in Decentralized or Centralized Exchanges. It is important that users understand those mechanisms very well before interacting with Levra Protocol.

## How is USDL price determined?

Because of it's design and the previously described recovery mode, it is likely that USDL will move around it's peg in decentralized markets in a range. This does not mean that the token cannot move below or above those ranges, and users should always be careful and fully aware of their actions when using Levra Protocol.

USDL can be defined as a _volatility dampened token_. This happens through a combination of mechanisms defined below:

### Hard peg

The ability to redeem USDL for collateral inside Levra's Vessels and to mint USDL at a 90% LTV against WETH creates a price floor and price ceiling respectively through arbitrage opportunities. We call these "hard peg mechanisms" since they are based on direct processes. This offers to the user a more forgiving margin of error to avoid redemption. More importantly, it allows USDL to not regularly be over peg, which would otherwise make over time the implementation of USDL in other protocols less desirable.

### Soft peg

USDL also benefits from less direct mechanisms — called "soft peg mechanisms". As the price of USDL fluctuates below and above 1 USD, opportunities arise for both borrowers and depositors.&#x20;

Another of these mechanisms is parity as a Schelling point. Because of it's design, actions taken by users interacting with the Smart Contracts developed by Levra Protocol will _always_ value 1 USDL as if it is worth $ 1 USD. Parity between the two is an implied (but not guaranteed) equilibrium state of the protocol.
