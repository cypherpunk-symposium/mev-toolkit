## block building on ethereum

<br>

### tl; dr

<br>

* with the advent of proposer-builder separation (pbs) in 2022, the role of an ethereum validator was split between block proposing and block building. 
* block builders are specialized actors who construct blocks from transaction orderflow, by ordering bundles in a block template (the execution payload) that maximizes profit.
    * a builder’s profit is determined by the sum of inclusion fees of transactions they can order in a block (without transaction revert).

##### block builders have the same sources of tx as validators did before the merge. they can:

1. include txs submitted to them privately, including from private or off-chain orderflow deals and those submitted by external searchers (through a "bribe" either by coinbase payments or `txsFees`).   
2. include pending tx broadcasted in the public mempool (**[which is dying 🪦](https://x.com/Data_Always/status/1882612445426180188)**)

##### in a high-level, a builder has the following roles:

1. win the block auction (to win the right to produce the block proposed at slot `n`, builders start competing at slot `n-1` by sending bids to the relays)
2. ensure privacy (e.g., not frontrunning)
3. ensure execution (e.g., position within block, atomicity of a bundle, non-revert)

##### the process is roughly the following:

1. builder creates a block by receiving transactions from users, searchers, or other (private or public) orderflow (block value, which is the amount of MEV the block is generating, and the maximum bid it can make).
2. the block is sealed (inserting the final payout tx and computing the root hash).
3. the builder submits the block to a **[relay](relays.md)**. the relay validates that the block is valid and calculates how much it pays the proposer. the relay sends a "blinded" header and a payment value to the proposer of the current slot. 
3. the proposer evaluates all the bids they’ve received and signs the blinded header associated with the highest payment. the proposer sends this signed header back to the relay. 
4. the block gets published by the relay using their local beacon nodes and returned to the proposer.
5. the rewards are distributed to the builder & proposer through transactions in the block and the block reward.

###### algorithms

* builders run algorithms designed to produce the most profitable block possible.
* block building is an np-hard problem, with reductions to both the **[knapsack problem](https://en.wikipedia.org/wiki/Knapsack_problem)** and the **[maximum weighted independent set problem](https://en.wikipedia.org/wiki/Independent_set_(graph_theory))**.
* examples of algorithms and goals:
    - effective gas price
    - overall block profit
    - purpose-made for a specific group’s bundle vs. associated with the submission of bundles from independent searchers
    - different merging algorithm strategies such as greedy classic, knapsack greedy, classic greedy informed solutions, distributed blockbuilding networks via secure knapsack auctions,...

###### reorg losses

* **[the ethereum network can fork for a short time, causing block reorgs](https://etherscan.io/blocks_forked)**. 
* in this case, all transactions from the losing fork go to the mempool (including private transactions, builder-generated transactions, including those added at the end of the block to pay the validator). the builder pays for the bid without winning a block.
* some ideas:
    - pay through a contract that reverts if the coinbase is NOT the builder’s address.
    - detect reorgs and post a transaction with same nonce

###### timing games

###### *"the equilibrium where everyone maximally plays timing games is not more favorable to any one validator than if everyone follows the protocol specifications honestly. however, there is money to be made on the path to the equilibrium by block proposers playing timing games more aggressively than others; thus the honest strategy is not an equilibrium."*

###### *"timing games present a challenge to decentralization and censorship resistance. they favor sophisticated entities like staking pools or centralized exchanges, who have the resources and size to experiment with risky strategies and ensure their late blocks remain on the canonical chain. these tactics aren't feasible for solo stakers, who can't afford the risk of missing a slot or engaging in such experimentation."* - t. wahrstätter

<br>

* **[timing games is a strategy](https://ethresear.ch/t/timing-games-implications-and-possible-mitigations/17612)** where block proposers and validators intentionally delay the publication of their block for as long as possible to maximize mev capture.
    * a block should be released at the beginning of the slot (`0` seconds into the slot, `t=0`).
    * the protocol selects a committee of attesters from the validator set to vote on the canonical block.
    * the honest behavior is requesting a block header at `t=0` (mev-boost) or requesting a block from the execution engine at `t=0`.
    * the specification dictates that the attestation is made as soon as they hear a valid block for their assigned slot, or `4` seconds into the slot (`t=4`), whichever comes first (`t=4` is as the attestation deadline.)
    * given the attestation deadline at `t=4`, a rational proposer needs to ensure a sufficient share of the attesting committee, 40%, votes for their block to avoid being reorged by the subsequent block proposer.
* t. wahrstätter created an awesome dashboard at **[timing.pics](https://timing.pics/)**, where one can see missed slots coinbase and bids selected by coinbase


<br>

----

### cool resources

<br>

#### specs and algorithms

* **[rbuilder: mev-Boost block builder in rust, by flashbots](https://github.com/flashbots/rbuilder)**
* **[builder specs, by the ef](https://github.com/ethereum/builder-specs)**
* **[mev-rs: gateway to a network of block builders, by a. stokes](https://github.com/ralexstokes/mev-rs)**

<br>

#### builders, data, stats

* **[fat stats for builders through mev-boost](https://www.mevpanda.com/)**
* **[rated.network's builders dashboard](https://www.rated.network/builders?network=mainnet&timeWindow=1d&page=1)**
* **[builder69.io endpoint for searchers (bundle/tx)](https://builder0x69.io)**
* **[etherscan blocks](https://etherscan.io/blocks)**, **[mev blocks](https://etherscan.io/blocks/label/mev-block)**, and **[mev builders](https://etherscan.io/accounts/label/mev-builder)**
* **[mev and the rise of builders, by galaxy (2023)](https://www.galaxy.com/research/whitepapers/mev-the-rise-of-the-builders/)**

<br>

#### decentralizing

* **[these days, things are very centralized by two major players (orderflow.art) (2025)](https://orderflow.art/?isOrderflow=true)**
* **[buildernet, by flashbots, beaverbuild, nethermind (2024)](https://buildernet.org/blog/introducing-buildernet)**
* **[decentralizing the builder role, by vub (2023)](https://hackmd.io/@vbuterin/distributed_builders#/)**
* **[the role of block building in the future of ethereum, by d. der werff (2023)](https://frontier.tech/beyond-extraction)**
* **[block builder decentralization is coming, but maybe not so soon, by ballsyalchemist (2023)](https://bittokoin.substack.com/p/block-builder-decentralization-is)**

<br>

#### algorithms and research

* **[buildernet, by flashbots (2024)](https://buildernet.org/docs)**
    * ppen-source block builder instances run by node operators, where instances share orderflow and coordinate their bids with each other. then orderflow providers can verify the builder instance software, and securely send orderflow to them (transactions stay provably private, with builder nodes running in tees).
* **[eip-7727, enable meta transactions to order other transactions, by l. johnson (2024)](https://eips.ethereum.org/EIPS/eip-7727)**
* **[from competition to centralization: the oligopoly in ethereum block building auctions, by wu et al. (2024)](https://arxiv.org/pdf/2412.18074)**
    * empirical game theoretic analysis exploring builders' strategic bidding incentives in MEV-Boost auctions, focusing on how advantages in network latency and access to MEV opportunities affect builders' bidding behaviors and auction outcomes.
* **[time is money: strategic timing games in pos protocols, by casparschwa et al. (2023)](http://arxiv.org/pdf/2305.09032)**
* **[timing games: implications and possible mitigations, by casparschwa (2023)](https://ethresear.ch/t/timing-games-implications-and-possible-mitigations/17612)**
* **[time to bribe: measuring block construction market, by a. wahrstätter et al. (2023)](https://arxiv.org/abs/2305.16468)**
* **[empirical analysis of the impact of block delays on the consensus layer, by aimxhaisse (2023)](https://ethresear.ch/t/empirical-analysis-of-the-impact-of-block-delays-on-the-consensus-layer/17888)**
* **[time, slots, and the ordering of events in ethereum pos, by g. konstantopoulos et al. (2023)](https://www.paradigm.xyz/2023/04/mev-boost-ethereum-consensus)**
* **[builder dominance and searcher dependence, by titan (2023)](https://frontier.tech/builder-dominance-and-searcher-dependence)**
* **[flashbots block building algorithm (2022)](https://writings.flashbots.net/searching-post-merge#blockbuilding-algorithm)**
* **[running geth within sgx, by flashbots (2022)](https://writings.flashbots.net/geth-inside-sgx)**
    
<br>

#### talks

* **[mev space #2: the searcher integration saga, by eigenphi (2025)](https://www.youtube.com/watch?v=gMhnyXp0CQM)**
 
