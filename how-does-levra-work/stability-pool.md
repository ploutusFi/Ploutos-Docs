# Stability Pool

## What is the Stability Pool?

The Stability Pool is the first line of defence in maintaining system solvency. It achieves that by acting as the source of liquidity to repay debt from liquidated Vessels — ensuring that the total USDL supply always remains backed.

When any Vessel is liquidated, an amount of USDL corresponding to the remaining debt of the Vessel is burned from the Stability Pool’s balance to repay its debt. In exchange, the entire collateral from the Vessel is transferred to the Stability Pool.

The Stability Pool is funded by users transferring USDL into it (called Stability Providers).

This allows for an interesting mechanic to play out: over time Stability Providers lose a pro-rata share of their USDL deposits, while gaining a pro-rata share of the liquidated collateral.

In the example of WETH Vessels, because those are likely to be liquidated at just above 90% LTV, it is expected that Stability Providers will receive a greater dollar-value of collateral relative to the debt they pay off.

For more information on the Collaterals that you can use with Levra Protocol [consult this page.](vessels-and-collateral.md)

## Why should I deposit USDL to the Stability Pool?

Stability Providers will earn profits from liquidations and may potentially receive GRVT tokens in the future.

Liquidation profits are inversely related to the LTV of the collateral type being liquidated on Levra. For instance, when a WETH Vessel is liquidated, users can anticipate acquiring WETH at approximately a 10% discount.&#x20;

Similarly, for an LST Vessels which allow users to borrow USDL at up to 85% TVL, Stability Providers can expect to obtain that LST at roughly a 15% discount upon liquidation.

## What are liquidations?

To ensure that the entire USDL supply remains fully backed by collateral, Vessels that go over the maximum LTV will be closed (liquidated).

The debt of the Vessel is cancelled and absorbed by the Stability Pool and its collateral distributed among Stability Providers.

The owner of the Vessel still keeps the full amount of USDL borrowed. However the user loses value overall: it is very critical, to avoid being liquidated, to always keep the ratio above the protocol set amount.

## Who can liquidate Vessels?

Anybody can liquidate a Vessel as soon as it goes above the maximum LTV defined by the protocol.\
\
The initiator receives a gas compensation `(200 USDL + 0.5% of the Vessel's collateral)` as reward for this service. This mechanism is in place to avoid excessive exposure of the liquidator to the gas costs that are incurred by performing this on-chain operation.

Our UI currently does not offer the possibility to liquidate Vessels. Please check our [Contract Addresses](..\about-levra-protocol\smart-contracts.md) if you wish to implement a service for liquidating Vessels.

The 200 USDL is funded by a Liquidation Reserve that users deposit into when opening their Vessel. The 0.5% part comes from the liquidated collateral, slightly reducing the liquidation gain for Stability Providers.

## How do I benefit as a Stability Provider from liquidations?

As liquidations happen just above a predefined LTV, you will most likely experience a net gain whenever a Vessel is liquidated as a Stability Provider.

Let’s say there is a total of `1,000,000 USDL` in the Stability Pool and your deposit is `100,000 USDL`. Now, a Vessel with debt of `200,000 USDL` and collateral of `400 WETH` is liquidated at an Ether price of `$545`, and thus at a LTV of \~`90% (= (200,000) / (400 * 545) * 100%)`. Given that your pool share is \~`10%`, your deposit will go down by `10%` of the liquidated debt (20,000 USDL), i.e. from `100,000` to `80,000 USDL`. In return, you will gain \~`10%` of the liquidated collateral, i.e. `40 WETH`, which is currently worth `$21,800`. Your net gain from the liquidation is `$1,800`.

Liquidation profits are inversely related to the Maximum LTV of the collateral type being liquidated on Levra. For instance, when a WETH Vessel is liquidated, users can anticipate acquiring WETH at approximately a \~10% discount.&#x20;

Similarly, for LSTs Vessels which allow users to borrow USDL at up to 85% LTV, Stability Providers can expect to obtain that LST at approximately a \~15% discount upon liquidation.

## Can I withdraw my deposit whenever I want?

As a general rule, you can withdraw the deposit made to the Stability Pool at any time. There is no minimum lockup duration. However, withdrawals are temporarily suspended whenever there are liquidatable Vessels with a LTV above the amount set by the protocol that have not been liquidated yet.

## Can I lose money by depositing funds to the Stability Pool?

While liquidations will occur at a LTV well below 100% most of the time, it is theoretically possible that a Vessel gets liquidated above 100% in a flash crash or due to an oracle failure. In such a case, you may experience a loss since the collateral gain will be smaller than the reduction of your deposit.

If USDL is trading above $1, liquidations may become unprofitable for Stability Providers even at LTV lower than 100%.&#x20;

Please note that although the system is diligently audited, a hack or a bug that results in losses for the users can never be fully excluded.

## What happens if the Stability Pool is empty when liquidations occur?

If the Stability Pool is empty, the system uses a secondary liquidation mechanism called redistribution. In such a case, the system redistributes the debt and collateral from liquidated Vessels to all other existing Vessels. The redistribution of debt and collateral is done in proportion to the recipient Vessel's collateral amount.
