# Vessels and Collateral

## What are Vessels?

A Vessel is where you can deposit collateral against which you can borrow GRAI and maintain your loan. Each Vessel is linked to an Ethereum address and each address can have just one Vessel per collateral type. If you are familiar with Vaults or CDPs from other platforms, Vessels are a similar concept.

Vessels maintain two balances: one is an asset acting as collateral and the other is a debt denominated in GRAI. You can change the amount of each by adding collateral or repaying debt. As you make these balance changes, your Vessel's LTV changes accordingly.

You can close your Vessel at any time (excluding the times when system is in Recovery Mode) by fully paying off your debt. You will find more information about Recovery Mode in the [System Status and Price Volatility page](system-status-and-price-volatility.md).

## Vessel Status

After you open a Vessel, Gravita Protocol displays your "Vessel Status".&#x20;

Inactive is displayed when no GRAI has been borrowed.

<mark style="color:green;">Active</mark> is displayed when when GRAI has been borrowed, and the Vessel has not been liquidated or redeemed against.

<mark style="color:yellow;">Redeemed</mark> is  displayed when a Vessel has been redeemed against for having a risky LTV. To find more information about Redemptions, look at our [Redemptions and Liquidations page.](redemptions-and-liquidations.md)

<mark style="color:red;">Liquidated</mark> is displayed when a Vessel has been liquidated for going above the maximum LTV. To understand how Liquidations work, [follow this link to our page.](redemptions-and-liquidations.md)

## Collateral ratio and Loan to Value Ratio

The terms Collateral Ratio and Loan-to-Value (LTV) ratio are both used to describe the relationships between the collateral, the borrowed amount, and the value of the collateral. Understanding the distinction between these two concepts is crucial for users who want to maintain a healthy position in the protocol.

### Collateral Ratio

The Collateral Ratio is the proportion of the total value of the Collateral to the total Value of the Borrowed amount. It is expressed as a percentage and indicates the degree to which the collateral backs the borrowed amount.

$$
\displaystyle{C}{R}={\left(\frac{{{C}{V}}}{{{B}{V}}}\right)}⋅{100}
$$

A higher Collateral Ratio means that the borrower has more collateral relative to the borrowed amount, which reduces the risk for the protocol.&#x20;

### Loan-to-Value (LTV) Ratio

The LTV ratio, on the other hand, is the proportion of the total value of the borrowed amount to the total value of the collateral. It is also expressed as a percentage and indicates the degree to which the borrowed amount is covered by the collateral.

$$
\displaystyle{L}{T}{V}={\left(\frac{{{B}{V}}}{{{C}{V}}}\right)}⋅{100}
$$

A lower LTV ratio implies a safer position for the borrower, as it means that they have more collateral relative to the borrowed amount, reducing the risk of liquidation. In Gravita Protocol, it is essential to maintain a healthy LTV ratio to avoid liquidations and ensure a smooth borrowing experience.

For simplicity and consistency, this documentation will always refer to LTV.

## Why would I want to put my collateral on Gravita Protocol?

### 1. Capital efficiency and Productive Collateral

Since less collateral is needed for the same loan, Gravita Protocol offers more capital efficiency than other decentralized lending platforms. Your productive asset continues to provide you with interest even when it is used as a collateral.&#x20;

This is also true for your LP positions that will be available to be used as a collateral in a future update.

Also, borrowers can increase their exposure to the LST of their choice by leveraging their position.

For example, the proceeds of loans issued in the form of GRAI can be used to purchase more collateral, that in return allows to mint more GRAI.

_**This is not a recommendation on how to use Gravita Protocol, use leverage at your own risk!**_

### 2. Collateral LTV

You can find here the maximum amount of GRAI that you can borrow based on your LST collateral of choice.

_**REMINDER: while Gravita Protocol is by design a multi-collateral lender, you can only borrow against a single LST for each Vessel that you open. If you wish to borrow GRAI using different tokens, you will need to open a separate vessel each time.**_

| Token  | Maximum LTV                    |
| ------ | ------------------------------ |
| WETH   | 90%                            |
| rETH   | 85%                            |
| wstETH | 85%                            |
| bLUSD  | 99% (with no liquidation risk) |

In addition mint caps are in place to ensure protocol stability. These numbers will be reviewed as the protocol grows and will be available [on the Gravita Protocol website.](https://www.gravitaprotocol.com/)

WETH liquidations will always be total liquidations.&#x20;

### 3. Fixed 0% APR

Many borrowing protocols offer a variable borrowing APR that is determined based on supply and demand. This can be quite inconvenient for users since they need to constantly check their position to avoid liquidation. As shown recently, variable APR can increase quite drastically and suddenly, which can cause a sub-optimal user experience.

With Gravita Protocol you can enjoy interest-free borrowing with a low maximum and fixed one time fee of 0.5% for positions longer than 6 months. Short term borrowers will be incentivized to use the protocol with a partial refund mechanism.

### 4. Fee refund for short term borrowers

When a user repays his debt before the expiry of six months (\~182 days), the 0.5% fixed borrowing fee is refunded pro rata for the time elapsed, but at least one week worth of interest.

The smart contract controls this decaying refund by immediately remitting the minimum fee (either to the Treasury or to a staking contract) and maintaining a record that includes the refund balance and the timestamp of the last change in the amount from the timestamp of the expiry date.

### 5. Peg Stability and Softer Redemptions

In order to reduce the volatility of GRAI, a Liquity-like redemption mechanism will be enabled after launch. More information is available on the [Redemptions and Liquidations](redemptions-and-liquidations.md) page.

You can find more on the [System Status and Price Volatility page.](system-status-and-price-volatility.md)

### 6. Decentralization

Make a difference in the Ethereum ecosystem by supporting minority liquid staking tokens - especially those emphasizing decentralization.

### 7. Oracles

Gravita uses Chainlink as an oracle. A fallback will be implemented soon after launch.
