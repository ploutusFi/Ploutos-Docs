# Risks

## Risks & Mitigants

When operating on the cutting edge, there are always risks involved. We believe these risks are both small and manageable, and that users can expect a safe and reliable service. However, it’s essential to discuss these risks and the mitigants in place to address them.

### **Collateral Callability**

In the event of liquidations, Levra will have the ability to withdraw assets on demand from the Levra x NodeSet Vault. This means there is minimal risk of any kind of gravETH discount to NAV (Net Asset Value) emerging on secondary markets, even if gravETH is traded on secondaries.

**Custodial Risk**

All technologies involved are entirely noncustodial. This means neither NodeSet nor its operators take custody of assets at any time, ensuring user control over their funds.

**Liquidations**

Liquidations are an inherent risk of leveraged positions, not unique to Levra. Levra’s liquidation mechanism automatically executes by burning USDL from the Stability Pool to cover the debt of over-leveraged borrowers. The USDL Stability Pool depositors then receive the liquidated collateral pro rata.

**LST Liquidity**

The risk of a sudden gravETH discount to NAV impacting borrowers due to an illiquid secondary market is extremely low. ETH can be withdrawn from the StakeWise vaults by gravETH token holders on demand. We do not expect a substantial discount even under unusual network circumstances. This risk can be entirely avoided if users prefer strategies without token involvement.

**Offline and Leaking Risk**

Offline validators slowly lose assets at the same rate as they accrue rewards when online. While small losses are possible during maintenance, NodeSet’s distributed operator base mitigates these effects. In serious cases, multiple safeguards cap losses at an estimated 0.7% of each offline validator. Only one inactivity leak has occurred in Ethereum’s history, resulting in minimal losses.

**Mitigants:**

* Maximal asset distribution across operators
* High operator skill and history
* Ease of validator operation
* Active operator network monitoring
* Pre-signed exit messages (NodeSet and StakeWise)

**Slashing Risk (Individual)**

Since the beacon chain launch in December 2020, there have been minimal slashing events across Ethereum’s validator set. Out of nearly 900,000 validators, only 105 unique slashing events have occurred, affecting a total of 405 validator keys with an average loss of 1.1 ETH per event.

**Mitigants:**

* Maximal asset distribution across operators
* High operator skill and history
* Ease of validator operation

**Slashing Risk (Correlated)**

While individual slashing events are rare, a correlated slashing event due to a major Ethereum client software bug could lead to significant losses. However, NodeSet’s diversification of client software among operators reduces this risk. Estimated maximum losses in such scenarios are approximately 7%, with more realistic damages less than 2%.

**Smart Contract Risk**

Smart contracts can be vulnerable to hacks and exploits. We only operate on fully audited infrastructure, tested by multiple parties before deployment on Ethereum mainnet.

**Audit Information:**

* **StakeWise v3:** Launched Nov 2023, audited by Hats, Halborn, and Sigma Prime in 2023.
* **Levra:** Launched May 2023, audited by Hats, Dedaub, and Omnicia in 2023.
* **NodeSet:** Uses widely used smart contract primitives developed by 0xSplits, audited by Macro in Feb 2022.

**Validator Queues**

Extreme demand for Ethereum staking may impact redemption timing and return accrual. High demand can delay new validator creation due to entrance queues, while extreme market volatility can create exit queues, causing LST prices to trade at a discount to NAV.

**Mitigants:**

* Active engagement with Ethereum researchers and other staking protocol teams to accelerate validator exits and reduce risk of NAV discounts.

Levra and NodeSet are committed to providing a safe, reliable service with these mitigants in place to address potential risks. We invite users to explore the opportunities offered by gravETH, combining advanced staking infrastructure with innovative financial strategies.
