---
description: VPoSDAO - an innovative DAO by Ecoball
---

# Consensus mechanism

Ecoball implemented a new consensus model: VPoSDAO, a Vote Proof of Stake (VPoS) algorithm implemented as a decentralized autonomous organization (DAO). It is designed to provide a decentralized, fair, and energy efficient consensus for blockchains. The algorithm works as a set of smart contracts written in Solidity.&#x20;

## Vote Proof of Stake <a href="vote-proof-of-stake" id="vote-proof-of-stake"></a>

Vote Proof of Stake (VPoS) extends the PoS model to allow individuals to stake tokens on candidates (potential validators). Candidates who collect most tokens have greater chance of becoming validators. Mining rewards are then divided by the validators and the staking entities (voters).

VPoS provides the opportunity for voters to stake(vote) on potential validators by staking tokens on them. Candidates are incentivized to maintain a good reputation in order to attract voters and increase their chances of becoming validators.

VPoS is proven in its ability to scale at the cost of limiting the number of validators in the network. Overall TPS of the network gets improved, block generation time is shorten, transactions can be processed quickly and efficiently.

While this creates a measure of centralization, researchers have argued that “a Byzantine quorum system of size 20 could achieve better decentralization than proof-of-work mining at a much lower resource cost.” In response to the problems of the VPoS consensus mechanism, optimizations are carried out to avoid behaviors that damage the system. Block production is distributed equally among the preset number of elected validators, rather than concentrated among a few mining pools.

## Decentralized Autonomous Organization (DAO) <a href="decentralized-autonomous-organization-dao" id="decentralized-autonomous-organization-dao"></a>

A DAO is a self-sustaining, virtual entity defined by “smart contracts that contain the assets and encode the bylaws of an entire organization”. All financial transactions, rules, and decisions are enacted and stored on the blockchain, creating a transparent and verifiable record. Rules are initially set forth in smart contracts, and members (participating token holders) interact according to these regulations to further the goals of the organization. Organizational rules can be modified through mechanisms contained in the on-chain contracts or through an off-chain governance process.

## VPoSDAO consensus model <a href="vposdao-consensus-model" id="vposdao-consensus-model"></a>

VPoSDAO consensus implements a layered PoS model connected by smart contracts on a public blockchain. Sybil control and incentives exist in smart contracts working within the EVM and the execution state is stored on a public chain implementing the VPOSDAO consensus. The underlying BFT consensus exists on the network protocol level. This model requires modifications to the BFT consensus algorithm implementations in the Ethereum client to facilitate information exchange between smart contracts and the consensus layer.

This includes communication relays regarding consensus faults and validator set management. The AuRa implementation is implemented and operational on the OpenEthereum client. It is also operational on the Nethermind Client v1.10.71+, with plans to migrate to a Nethermind powered network with the upcoming deprecation of OpenEthereum support. HBBFT may also be implemented in a future release.

VPoSDAO is implemented with a general purpose BFT consensus protocol such as Authority Round (AuRa) with a proposer node and probabilistic finality, or Honey Badger BFT (HBBFT), leaderless and with instant finality. Validators are incentivized to behave in the best interests of a network through a configurable reward structure. The algorithm provides a Sybil control mechanism for managing a set of validators, distributing rewards, reporting and penalizing malicious validators.

It is compatible with a number of consensus algorithms. Chains may choose the underlying algorithm that best suits their use cases and users. For example, AuRa provides a consistent block rate whereas Honey Badger BFT produces varying block rates based on network performance. One of these variants may be advantageous based on the purpose of the network. Note that the AuRa implementation will be completed first, with HBBFT planned for a future release.

## Reward Structure <a href="reward-structure" id="reward-structure"></a>

### Minimum candidate stake <a href="minimum-candidate-stake" id="minimum-candidate-stake"></a>

The minimum candidate stake discourages the potential centralization of candidate seats, where individuals may attempt to register many candidate nodes and thus control a large percentage of validator sets. A high minimum candidate stake also deters a malicious set of validators from attempting a coordinated validator set attack. This value is configurable based on the network purpose and size .

Each validator pool within a validator set receives an equal share of the block reward\*. While a higher stake impacts the odds of a candidate pool becoming a validator pool, each validator pool receives the same reward. This creates parity among the validators participating in each staking epoch.

_Note: shares will only be equal if every validator produces blocks continuously. If a validator skips blocks, their pool will receive proportionally less reward than other (continuously working) validators. For example, if there are two validators in the validator set and one of them produced 10 blocks, but another only 5 blocks, the first validator's pool will receive 10/(10+5)=66% of the total reward, and the second pool will receive the remaining 34%._
