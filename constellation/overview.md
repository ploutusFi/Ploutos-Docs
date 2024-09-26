---
description: >-
  Constellation is a second-layer staking protocol built on top of Rocket Pool,
  initially developed by NodeSet.
---

# Overview

Constellation aims to extend Rocket Pool's capabilities by providing more benefits and optionality to users, improving capital efficiency and scalability, and reducing asset concentration risk. Constellation introduces liquid staking tokens, xrETH and xRPL, which offer unique properties compared to traditional liquid staking tokens (LSTs).\
\
**The Problem**\
\
To be maximally trustless, Rocket Pool requires naode operators to post a bond for each validator. This restricts growth by requiring a constant supply of NOs who can afford this bond and leads to an uneven distribution of assets across nodes.

**The Solution**

Constellation liquidizes the NO bond, opening it up to external investors via tokens called xrETH and xRPL. The ETH and RPL deposits used to mint these tokens are used by the Constellation smart contracts to create new minipools on Rocket Pool which are operated non-custodially by NodeSet operators.\
\
This allows to:

1. **Increase capital efficiency:** By enabling more ETH to be staked through a liquid staking token, xrETH, without requiring individual node operators (NOs) to lock large amounts of collateral.
2. **Minimize asset concentration risk:** By distributing assets across a large network of decentralized node operators.
3. **Enable external investors to participate in node bonding:** By tokenizing node operator bonds through xrETH and xRPL, Constellation enables external investors to fund the bonds that would normally be provided by the NOs themselves. This allows for more validators to be spun up, expanding the supply of rETH and xrETH.

<figure><img src="../.gitbook/assets/image (76).png" alt=""><figcaption><p>Constellation + Rocket Pool Architecture (simplified)</p></figcaption></figure>

There are four main user roles in this system:

1\) Depositors ([xrETH](https://docs.nodeset.io/constellation/xreth) or [xRPL](https://docs.nodeset.io/constellation/xrpl) holders)&#x20;

2\) [Node operators](https://docs.nodeset.io/constellation/node-operators)&#x20;

3\) [Administrator](https://docs.nodeset.io/constellation/administrator)&#x20;

4\) [Treasurer](https://docs.nodeset.io/constellation/treasurer)

