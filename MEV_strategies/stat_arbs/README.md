## statistical strategies (signal-based)

<br>

### tl; dr

<br>

* **statistical mev** (non-atomic) convey informed strategies that rely on off-chain information (signal)
* examples can be strategies that rely on:
   - **[cross-chains](https://github.com/autistic-symposium/mev-toolkit/tree/main/MEV_searchers/cross_domain_mev)** mev
   - **[defi-cefi arbitrage](dex-cex-arb/)**
   - **[order flow](https://github.com/autistic-symposium/mev-toolkit/tree/main/MEV_searchers/order_flows)** trading by aggregating from private and public mempools
   - **[whale watching](https://github.com/autistic-symposium/mev-toolkit/tree/main/MEV_and_trading/whales)** 
* these strategies are more profitable and less accessible due to capital requirements and risk profile

<br>

<p align="center">
<img src="https://user-images.githubusercontent.com/1130416/219130514-10104aa3-6219-45ff-8f93-e138d4085216.png" width="50%" align="center" style="padding:1px;border:1px solid black;"/>
</p>

<br>

----

### in this dir

<br>

* **[dex-cex arbitrage](dex-cex-arb/)**
* **[routers and aggregators](aggregators)**
* **[convex optimization](convex_optimization)**

<br>

---

### cool resources

<br>

* **[cross-chain arbitrages in the realm of blockchain interoperability, by b. oz et al. (2025)](https://arxiv.org/abs/2501.173350)**
   * systematic study of two non-atomic cross-chain arbitrage strategies (sequence-independent arbitrage and sequence-dependent arbitrage.
   * "analysis reveals that 32.88 % of ethereum legs in crosschain arbitrages were submitted privately (private mempools), yielding an average profit of 82.5 USD, compared to 78.35 USD for public transactions."
* **[anatomy of stat bots](https://github.com/go-outside-labs/mev-toolkit/blob/main/MEV_searchers/bots/stat-arbers.md)**
* **[`addLiquidity()` sandwich attack optimization problem](https://mirror.xyz/0xc19565163aFdEe3783FC970E4Bd0275B11848d34/oTdSfZEBdp9WPCNaKqDKCkuDJ9neR2UISc_5mMjZKYU)**
* **[dex arbitrage, mathematical optimizations & me, by noxx](https://noxx.substack.com/p/dex-arbitrage-mathematical-optimisations)**
* **[a new game in town, by frontier research](https://frontier.tech/a-new-game-in-town)**
* **[statistical arbitrage on amms and block building on ethereum – part 1, by greenfield](https://greenfield.xyz/2024/09/10/statistical-arbitrage-on-amms-and-block-building-on-ethereum-part-1/)**
* **[insights from 2 years of mev boost data, by p. stichler](https://www.youtube.com/watch?v=KcEZHQiopTg)**
