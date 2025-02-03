## mev on arbitrum

<br>

### tl; dr

<br>

* remember that optimistic rollups publish batches of txs in the calldata on ethereum, but it needs to wait for a dispute period to pass to ensure the sequencer is not publishing invalid txs before withdrawing.
* avm architecture: arbitrum is fully compatible with the evm, but it also has its vm called arbitrum virtual machine:
  * execution flow and structure: arbitrum has an operating system and its core called arbos, which ensures the solitary existence, optimal performance and efficient analytics of smart contracts.
  * dispute settlement speed: the avm has a custom protocol for dispute management, so that it can be acquired out on a standard vm.
  * natives tuples: the avm uses tuples to define and references types in its merkle tree. the tuples can be referenced in looking up the merkle root of any tx on the evm merkle tree. 
* optimistic rollup, with no mempool for bots to frontrun, but searchers can listen the queue through websockets and backrun, etc...
* currently has a centralized sequencer and whitelisted proof validation while having upgradable contracts
* faster tx processing: ethereum is operating under 15-20 tps, while the arbitrum network can process ~40 tps
* lower tx fees: in ethereum, a significant percentage of validators need to confirm the genuineness of a tx; arbitrum average fee is $~.2 compared to $6.5 (source: **[nansen](https://pro.nansen.ai/multichain/eth-vs-arbitrum)**)
 
<br>

----

### chapters

<br>

* **[gmx and glp vaults](gmx)**
* **[fair order sequencing](fair_ordering_sequencing)**

<br>

---

### cool resources

<br>

* **[understanding lvr on l2 blockchains, by e. hu (2025)](https://x.com/elenahoolu/status/1883634105637888030)**
* **[arbtrium latency war drama, by snoopy (2023)](https://twitter.com/snoopy_mev/status/1629283898453811200?s=20)**
* **[time boost: a new tx ordering policy proposal, by edfelten (2023)](https://research.arbitrum.io/t/time-boost-a-new-transaction-ordering-policy-proposal/8173)**
* **[transaction ordering policy, by edfelten (2022)](https://research.arbitrum.io/t/transaction-ordering-policy/127)**

<br>

##### docs

* **[arbitrum gas fee, by dune](https://dune.com/blog/fueling-gas-spells-arbitrum)**
* **[arbitrum bridge tutorial](https://arbitrum.io/bridge-tutorial/)**
* **[a closer look at the sequencer's role and mev, by p. mccorry](https://docs.google.com/presentation/d/1bU01VT7YyLXT0Bzxo0dRNYSEohmuKxY8ziErTviIsng/edit#slide=id.g1255a01e809_0_0)**
