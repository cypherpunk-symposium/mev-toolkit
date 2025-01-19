## block builders on ethereum

<br>

### tl; dr

<br>

* block builders have the same 3 sources of tx as validators did before the merge. they can:
    1. act as searchers and include their own MEV-extracting transactions.
    2. include txs submitted to them privately, including those submitted by external searchers (through a "bribe" through either coinbase payments or `txsFees`).   
    3. include pending tx broadcasted in the public mempool
* `blockValue` = `txFees` + MEV
* builders will aggregate txs from users, MEV searchers, and own private order flow to make the highest value blocks possible
* builders having its blocks included consistently incentivizes more private order flow (searchers want their tx included)
* builder can be selling future blockspace upfront so market makers or protocols can secure block space for their transactions or users


<br>
<img width="530" src="https://user-images.githubusercontent.com/1130416/217417346-50916961-aaa2-49ef-ad10-2f623a959fa6.png">
<br>

----

### cool resources

<br>

#### specs and algorithms

* **[builder specs, by the ef](https://github.com/ethereum/builder-specs)**
* **[builder opens source, by flashbots](https://github.com/flashbots/builder)**
* **[mev-rs: gateway to a network of block builders](https://github.com/ralexstokes/mev-rs)**
* **[flashbots block building algorithm (2022)](https://writings.flashbots.net/searching-post-merge#blockbuilding-algorithm)**

<br>

#### builders, data, stats

* **[fat stats for builders through mev-boost](https://www.mevpanda.com/)**
* **[rated.network's builders dashboard](https://www.rated.network/builders?network=mainnet&timeWindow=1d&page=1)**
* **[builder69.io endpoint for searchers (bundle/tx)](https://builder0x69.io)**
* **[etherscan blocks](https://etherscan.io/blocks)**, **[mev blocks](https://etherscan.io/blocks/label/mev-block)**, and **[mev builders](https://etherscan.io/accounts/label/mev-builder)**
* **[mev and the rise of builders, by galaxy (2023)](https://www.galaxy.com/research/whitepapers/mev-the-rise-of-the-builders/)**

<br>

#### decentralizing

* **[decentralizing the builder role, by vub (2023)](https://hackmd.io/@vbuterin/distributed_builders#/)**
* **[the role of block building in the future of ethereum, by d. der werff (2023)](https://frontier.tech/beyond-extraction)**
* **[block builder decentralization is coming, but maybe not so soon, by ballsyalchemist (2023)](https://bittokoin.substack.com/p/block-builder-decentralization-is)**
* **[buildernet, by flashbots, beaverbuild, nethermind (2024)](https://buildernet.org/blog/introducing-buildernet)**

<br>

#### research

* **[running geth within sgx, by flashbots (2022)](https://writings.flashbots.net/geth-inside-sgx)**
* **[eip-7727, enable meta transactions to order other transactions, by l. johnson (2024)](https://eips.ethereum.org/EIPS/eip-7727)**
* **[from competition to centralization: the oligopoly in ethereum block building auctions, by wu et al. (2024)](https://arxiv.org/pdf/2412.18074)**
    * empirical game theoretic analysis exploring builders' strategic bidding incentives in MEV-Boost auctions, focusing on how advantages in network latency and access to MEV opportunities affect builders' bidding behaviors and auction outcomes.

<br>

#### talks

* **[mev space #2: the searcher integration saga, by eigenphi (2025)](https://www.youtube.com/watch?v=gMhnyXp0CQM)**
 
