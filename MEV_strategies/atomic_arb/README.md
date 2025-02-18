## atomic arbitrage

<br>

### tl;dr

<br>


* in **tradefi**, arbitrage refers to buying something in one venue and selling it in another (through a series of intermediate transactions) for a higher price. this is note risk-free as prices can move mid-transaction.

* due to the nature of the evm's atomic execution, **atomic arbitrages** are possible (as opposed to tradefi): smart contracts allow the packaging a sequential execution of txs, for a set of conditions. if the conditions are not met, the execution can fail, undoing all the on-chain interactions that just occurred.

* since **liquidity on-chain is fragmented** (thousands of pools don't communicate with each other, each providing quotes for swapping assets in real-time), it creates an opportunity to buy low and sell high across different pools. for example, two DEXes offer a token at two different prices so that a token can be bought at the lower-priced DEX and sold on the higher-priced DEX in a single atomic transaction.

* **non-atomic (cross-chain, CEX/DEX, etc.) arbs** are covered **[here](https://github.com/go-outside-labs/mev-toolkit/tree/main/MEV_strategies/stat_arbs)**.

<br>

----

### in this dir

<br>

* [arbitrage patterns](patterns)
* [arbitrage algorithms](algorithms)
* [cool arb txs in the wild](mev_bots_wild)


<br>

----

### links

<br>

* **[atomic execution is not enough for arbitrage profit extraction in shared sequencers, by m. silva (2025)](https://www.youtube.com/watch?v=yhzMvaHhAOQ)**
* [anatomy of arber bots](https://github.com/go-outside-labs/mev-toolkit/blob/main/MEV_searchers/bots/arbers.md)
* [analyzing mev bot's arb, by et](https://medium.com/@etdu/analyzing-an-mev-bots-arbitrage-on-ethereum-c6980cfd347)
* [how to automate triangular arb recognition](https://mirror.xyz/0xc19565163aFdEe3783FC970E4Bd0275B11848d34/5-tFRGLVbVq0uCLnWnw7B0D-mD7GKZr1DfPXhyopU0Y)
* [cyclic arb in dexes, by wang et al](https://arxiv.org/pdf/2105.02784.pdf)
* [recoginizing atomic arbitrage mev, by eigenphi](https://eigenphi.substack.com/p/nerd-alert-the-upgraded-algorithm)


