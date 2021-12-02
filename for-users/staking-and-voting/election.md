---
description: This page provides a full introduction to Ecoball validator election
---

# Election

Link to election page: [https://scan.ecoball.org/validators](https://scan.ecoball.org/validators)

### **Validator**

A validator is a person who runs a node to verify and record transactions on Ecoball chain blocks.

Before elected to be a validator, one is identified as a candidate.

If a candidate wish to become a validator, he must stake 500,000 ECO in his pool (must be on a new address), then launch a candidate pool for voters to stake to.

Once the above set up is been done, the candidate will get a chance to be elected in each 28800 block cycle (≈one day). Successful candidate (get elected) will be rewarded with 2% of the pool service fees.

&#x20;

### **Candidate**

If there are over 25 (i.e. 26 or above) qualified candidates, then 25 candidates will be selected to be validators according to staked amount in their pool. The greater the staked amount is, the higher chance a candidate gets elected.

The maximum number of candidates is 3000.



### **Voter**

A voter is an ECO owner who stakes his ECO in validator/candidate pools. If the chosen candidate is elected to be a validator, the voter gets rewards as well. By staking ECO, voters will vote for their best interest, and a minimum amount of 1000 ECO will be required for each vote.

&#x20;

### **Staking Cycle (Election Cycle)**

One staking cycle lasts approximately one day, or 28800 blocks, with a releasing speed of three seconds per block.

&#x20;

### **Election Mechanism**

An election cycle has 28800 blocks (≈24 hours, 3 seconds per block). At the end of each cycle, 25 candidates will be elected and become validators based on their staking amount. Any staking amount greater than 5,000,000 will be counted as 5,000,000 (the ceiling).

&#x20;

### **Stake, Unstake, Move functions disabled**

Each cycle breaks down into a votable period and a non-votable period. A non-votable period is the last 2400 blocks. In a non-votable period, stake/unstake/move functions will be disabled to avoid cheating. The action buttons (stake/unstake/move) will be hidden until next cycle.

&#x20;

### **Claim staking rewards**

The reward cycle breakdown:

&#x20;   \-    T (staking cycle, current block creation cycle)

&#x20;   \-    T+1 (block creating and rewarding cycle),

&#x20;   \-    T+2 (rewards claimable cycle).

At T, voters stake for candidates. If at T+1, the candidates are elected to be validators, voters start getting rewards. At T+2, voters can claim rewards.

&#x20;

### **Rewards Calculation**

For each cycle, the amount of ECO rewards is calculated with formula:

&#x20;                                               _y = a - b \*（T-1）_

Where _**a - initial reward，b – decreasing factor , T - the current cycle**_

&#x20;              _**a**_ is fixed at 80547.945205479452054794

&#x20;              _**b**_ is fixed at 2.206793019328204165

&#x20;              _**T**_ is the current cycle (‘Epoch number’ on validators page)

At the 18251st cycle, the reward will be fixed at 40273.97260273973:

&#x20;            _If T <= 18250, reward = a - b \*（T-1）_

&#x20;            _If T > 18250, reward = 40273.97260273973_

&#x20;

### **Rewards Distribution**

Follow the above calculation method, **a total amount of rewards (y)** will be calculated for each cycle, then the total rewards will be distributed according to ECO stake amount of each pool.

_Individual Pool Rewards = ( y / 28800 ) \* Number of Blocks Created by the Pool_

_Pool Owner Rewards = Individual Pool Rewards \* (2% + Owner’s Staking / Total Individual Pool Staking)_

_Individual Voter Rewards = ( Individual Voter Staking / Total Pool Staking ) \* 98% of Individual Pool Rewards_

&#x20;

### **Penalty**

Each validator node is obligated to generate random numbers. In each cycle (28800 blocks), a validator node needs to generate 48 random numbers (28800 / 600, 600 blocks per random number – 600 is a random number _**collectRound**_** ** length).

At the end of a cycle, the system will count random numbers that are skipped by a validator node and record the count as _**skipNumber**_. Sometimes a node could run into malfunction, to avoid false penalty, the first three _**collectRound** _ will not be counted, and 2 _**skipNumber** _ will be remitted (_**skipNumber** _ -= 2_)_.

Since the last random number will affect election result, therefore if a validator node skips the last random number, it will be penalized 10 additional counts (_**skipNumber** _ += 10).

If _**skipNumber**_ > 0, the node will be banned for _**skipNumber**_ \* 5 cycles. ECO on the node will be locked up as well.

&#x20;

### **Inactive pool**

Under below conditions, an active pool will be moved to the inactive pool list:

1\.      The validator/candidate exit the node, the pool will become inactive. Pool participants will only be able to unstake and claim rewards.

2\.      Unexpected events happen during block release, leading to a block release failure. The malfunctioned pool will be moved to the inactive pool list in next cycle with a lock-up penalty.

During the lock-up period, pool participants are not allowed to unstake and claim rewards.

It is strongly recommended that validators/candidates check and ensure their nodes are under good conditions all the time.

&#x20;

&#x20;

&#x20;
