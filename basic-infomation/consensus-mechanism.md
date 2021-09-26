# Consensus mechanism

In this paper we introduce VPOSDAO, a Vote Proof of Stake \(VPOS\) algorithm implemented as a decentralized autonomous organization \(DAO\). It is designed to provide a decentralized, fair, and energy efficient consensus for public chains. The algorithm works as a set of smart contracts written in Solidity. VPOSDAO is implemented with a general purpose BFT consensus protocol such as Authority Round \(AuRa\) with a proposer node and probabilistic finality, or Honey Badger BFT \(HBBFT\), leaderless and with instant finality. Validators are incentivized to behave in the best interests of a network through a configurable reward structure. The algorithm provides a Sybil control mechanism for managing a set of validators, distributing rewards, and reporting and penalizing malicious validators.

VPOSDAO is compatible with a number of consensus algorithms. Chains may choose the underlying algorithm that best suits their use cases and users. For example, AuRa provides a consistent block rate whereas Honey Badger BFT produces varying block rates based on network performance. One of these variants may be advantageous based on the purpose of the network. Note that the AuRa implementation will be completed first, with HBBFT planned for a future release.

## Proof of Stake model <a id="proof-of-stake-model"></a>

Consensus algorithms provide an economic incentive for honest protocol execution and decentralization. In a Proof of Stake \(POS\) model, individuals stake an amount of tokens in an effort to be selected as a block producer \(validator\). Validators are chosen based on numerous criteria; typically the amount of stake and a randomness beacon are used in the selection process. In exchange for successful block creation, validators are rewarded with additional tokens.

A main advantage of a POS Sybil resistant system is the reduced energy expenditure in comparison to a Proof of Work \(POW\) model. Additionally, POS incentivizes validators to run high-bandwidth nodes and backup nodes for redundancy, which improves network throughput. POW, on the other hand, incentivizes the purchase of more mining hardware, which does not improve the maximum throughput.

There are two major POS models: Chain-based proof of stake, which “\[..\] features a chain of blocks and simulates mining by pseudorandomly assigning the right to create new blocks to stakeholders, and Byzantine Fault Tolerant \(BFT\) proof of stake, where an existing BFT consensus is repurposed for Sybil control and economic incentive models”. POSDAO utilizes smart contracts for the validator selection process. These validator sets then run the underlying consensus protocol. It can be configured to use OpenEthereum's AuRa consensus engine or Honey Badger BFT.

## Vote Proof of Stake <a id="vote-proof-of-stake"></a>

Vote Proof of Stake \(VPOS\) extends the POS model to allow additional individuals to stake their tokens on potential validators \(candidates\), without participating in block production themselves. Candidates who collect a higher percentage of tokens have greater odds of becoming validators on the network. Rewards are then divided amongst the validators and the staking entities \(Voters\).

VPOS provides the opportunity for Voters to “vote” on potential validators by staking tokens on them. Candidates are incentivized to maintain a good reputation in order to attract more Voters and increase their chances of becoming validators.

VPOS is known to provide a high level of scalability at the cost of limiting the number of validators on the network. While this creates a measure of centralization, researchers have argued that “a Byzantine quorum system of size 20 could achieve better decentralization than proof-of-work mining at a much lower resource cost.” Block production is distributed equally among the preset number of elected validators, rather than concentrated among a few mining pools. Transactions can be processed quickly and efficiently, creating a highly scalable solution.

## Decentralized Autonomous Organization \(DAO\) <a id="decentralized-autonomous-organization-dao"></a>

A DAO is a self-sustaining, virtual entity defined by “smart contracts that contain the assets and encode the bylaws of an entire organization”. All financial transactions, rules, and decisions are enacted and stored on the blockchain, creating a transparent and verifiable record. Rules are initially set forth in smart contracts, and members \(participating token holders\) interact according to these regulations to further the goals of the organization. Organizational rules can be modified through mechanisms contained in the on-chain contracts or through an off-chain governance process。

## VPOSDAO consensus model <a id="vposdao-consensus-model"></a>

VPOSDAO consensus implements a layered POS model connected by smart contracts on a public blockchain . Sybil control and incentives exist in smart contracts working within the EVM and the execution state is stored on a public chain implementing the VPOSDAO consensus. The underlying BFT consensus exists on the network protocol level. This model requires modifications to the BFT consensus algorithm implementations in the Ethereum client to facilitate information exchange between smart contracts and the consensus layer.

This includes communication relays regarding consensus faults and validator set management. The AuRa implementation is implemented and operational on the OpenEthereum client. It is also operational on the Nethermind Client v1.10.71+, with plans to migrate to a Nethermind powered network with the upcoming deprecation of OpenEthereum support. HBBFT may also be implemented in a future release.

## Reward Structure <a id="reward-structure"></a>

### Minimum candidate stake <a id="minimum-candidate-stake"></a>

The minimum candidate stake discourages the potential centralization of candidate seats, where individuals may attempt to register many candidate nodes and thus control a large percentage of validator sets. A high minimum candidate stake also deters a malicious set of validators from attempting a coordinated validator set attack. This value is configurable based on the network purpose and size .

Each validator pool within a validator set receives an equal share of the block reward\*. While a higher stake impacts the odds of a candidate pool becoming a validator pool, each validator pool receives the same reward. This creates parity among the validators participating in each staking epoch.

_Note: shares will only be equal if every validator produces blocks continuously. If a validator skips blocks, their pool will receive proportionally less reward than other \(continuously working\) validators. For example, if there are two validators in the validator set and one of them produced 10 blocks, but another only 5 blocks, the first validator's pool will receive 10/\(10+5\)=66% of the total reward, and the second pool will receive the remaining 34%._

