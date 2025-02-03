## flashbots

<br>

### tl;dr

<br>

* **flashbots** is a research and development organization focused on mitigating the negative externalities of current MEV extraction techniques.
* after the release of MEV-geth (and later MEV-boost), much of the computation related to MEV was taken off-chain, by a side-relay that allows MEV searchers to communicate directly with nodes and other participants. This lead to a decrease in fee congestion pricing.
* however, MEV “marketplaces” like flashbots, are quite centralized, since the vast majority of blocks flow through it.

##### bundles

* bundle/transaction profitability is determined by: fee per gas used, priority fee, and direct validator payments.

<br>

----

### chapters

<br>

* **[mev-boost](mev-boost)**
* **[suave](suave)**
* **[scripts](scripts)**
* **[tools](tools)**

<br>

---

### cool resources

<br>

* **[protecting against mev with flashbots, c. chapman et al (2025)](https://x.com/i/broadcasts/1MnxnDwrjNLGO)**
* **[mev economics videos, by eth global (2024)](https://www.youtube.com/playlist?list=PLXzKMXK2aHh7bW0j2dhpnLNiIJIMnPgsD)**
* **[order flows kingmaker of block builders, by noxx (2022)](https://noxx.substack.com/p/order-flows-kingmaker-of-the-block)**

<br>

##### docs

* **[bundle pricing docs](https://docs.flashbots.net/flashbots-auction/searchers/advanced/bundle-pricing)**
* **[flashbots' research topics](https://github.com/flashbots/mev-research)**

<br>

##### code

* **[data analysis of flashbots mev](https://github.com/ivanmolto/mev-flashbots-unleashed)**



