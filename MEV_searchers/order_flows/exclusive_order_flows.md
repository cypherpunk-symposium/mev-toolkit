##  exclusive/private order flows 

<br>

### tl; dr

<br>

* searchers who have access to private and public mempools can aggregate txs and predict price movement.
* market makers (lps) can use order flows to model information from incoming orders and readjust prices and spreads.
* traders can use order flow sas a short-term strategy to time their trade.

<br>

#### types of private order flows

<br>
<center>
<img width="500" src="https://user-images.githubusercontent.com/1130416/217937850-9b7e9434-ee72-4c2a-9e5e-ae9fe795310e.png">
</center>
<br>

##### rpc-based "payment for order flow protocols" (POFPs)

* this type of private order flows can be realized by modifying either the user's rpc or by modifying the protocol's frontend
* the rpc endpoint re-broadcasts (forwarding) the tx to nodes. 
* in respect to every pending tx they receive, they can: 1) censor, 2) forward to some mempool, or 3) forward it directly to some block-builders or validators.

<br>

##### validator transaction reordering protocols (VTRPs)

* private tx reordering
* two goals: 1) identify valuable user txs, 2) replace the POFP's value-extracted tx with its own value-extractive tx
* when a VTRP is able to identify a valuable user tx but, due to the tactics of the POFP, is unable to inject its own transaction in place of the POFP's -> VTRP's optimal strategy is to censor the user's transaction from the final block

<br>

---

### cool resources

<br>


* **[the orderflow auction design space, by frontier (2023)](https://frontier.tech/the-orderflow-auction-design-space)**
* **[private order flow and the block builder market, by j. charbonneau (2022)](https://twitter.com/jon_charb/status/1562916372505665536)**
* **[ethereum's biggest issue no one's talking about, by mvd wijden (2022)](https://mariusvanderwijden.github.io/blog/2022/10/21/lightclients/)**
* **[private order flow is the new mev (video), by empire (2022)](https://www.youtube.com/watch?v=bapIqxhIdaY)**
* **[order flow, auctions and centralisation II: order flow auctions, by quintus (2022)](https://collective.flashbots.net/t/order-flow-auctions-and-centralisation-ii-order-flow-auctions/284)**
* **[order flow auctions & enshrined builder, by apriori (2022)](https://mirror.xyz/apriori.eth/wiLKgkaN6JBwBDq4E3T_-BZ0OIPhlbIItgJdE3CFAMo)**

