# Tokenomics

**This page introduces ECO and the tokenomic.**

## What is ECO? <a href="#what-is-eco" id="what-is-eco"></a>

ECO is the native token of the Ecoball ecosystem. It serves as a unit of account and assumes the functionalities of payment for network utility, security checking and governance.

Any transaction on the Ecoball chain will consume ECO, similar to gas fees consumed on other networks; however, in case of malicious attacks, a large amount of ECO will be consumed, making the attacker unable to sustain. This mechanism endows ECO the power to safeguard the Ecoball blockchain.

ECO holders provide ECO as collateral when participating in the VPoS consensus process. In exchange for providing ECO (to stake in a node), users receive mining rewards. The reward is in the form of additional ECO tokens.

As the network develops, ECO will be used for chain governance where holders could vote to update network parameters. This will include items such as validator/delegator minimums, fees, etc.

## ECO Token Economics

### 1.1. Quantity

Circulating Supply: 193 million ECO

Total Current Supply: 330 million ECO

![](../.gitbook/assets/tokenomics.PNG)

### 1.2. Mining Rules

In the early stage of the community, pioneer miners deserve higher rewards. To reward these pioneers, we adopt an ECO releasing schedule with a linear decreasing model, early miners will receive more ECO per block as rewards. Going forward as the platform become stable and robust, ECO releasing amount will gradually decrease on a per block basis.

The formula to calculate block rewards (ECO release) during each voting cycle:

![Where T represents the block height.](../.gitbook/assets/0.6.PNG)

Below are illustrations of the mining reward rules:

![the total supply amount of ECO (y-axis) over years (x-axis) without deflation caused transaction fees burning.](../.gitbook/assets/image\_2021-12-09\_10-43-56.png)

![Block rewards (y-axis) to miners (including validators and voters) will be released linearly within 30 years (x-axis) after the mainnet launch](../.gitbook/assets/2.PNG)

### 1.3. Staking Rewards

A key indicator to the robustness of a Proof-of-Stake system is the staking ratio of the network. A high staking ratio will make the system hard-to-attack. However, once the staking ratio pass a point where it becomes too high, the system will be overwhelmed, consequently, liquidity in the system will be decreased. Therefore, in the long run, the staking ratio will dynamically adjust itself to reach equilibrium. Referring to current PoS public blockchains, the equilibrium point should be where the staking ratio is between 0.5 and 0.6.

The self-balancing mechanism of the staking ratio is realized by the negative correlation between the staking yield and the staking ratio. When the staking ratio drops, the staking yield will increase to encourage more users to stake; when the staking ratio increases, the staking yield will drop for users to seek other opportunities. The security and stability of the system is maintained through such mechanism.

The following chart illustrates an estimation of staking yields vs staking ratios:

![Estimated staking yields versus different staking ratios](../.gitbook/assets/3.PNG)
