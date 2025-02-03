## mev-boost relays

<br>

### tl; dr

* on ethereum post-merge, relays act as trusted auctioneers between block proposers and block builders, validating blocks received by block builders and forwarding only valid headers to validators/proposers.
  * this ensures validators cannot steal the content of a block builder’s block, but can still commit to proposing this block by signing the respective block header.
* when the proposer chooses to propose a block, the proposer requests `getHeader` to receive the highest bidding, eligible block header from the relay.
  * upon receiving the header associated with the winning bid, the proposer signs it and thereby commits to proposing this block built by the respective builder in slot `n`.
  * the signed block header is sent to the relay, along with a request to get the full block content from the relay (`getPayload`).
* finally, the relay receives the signed block header (`signedAt`) and publishes the full block contents to the p2p network and proposer. when peers see the new block, validators assigned to the slot can attest to it.

<br>

---

### cool resources

<br>

##### specs and docs

* **[mev relay list, by ethstaker](https://github.com/eth-educators/ethstaker-guides/blob/main/MEV-relay-list.md)**
* **[mev relay list, by beaconcha.in](https://beaconcha.in/relays)**
* **[mev relay ofac watch, by labrys](https://www.mevwatch.info/)**
* **[mev-boost relay data, by t. wahrstätter](https://mevboost.pics/)**
* **[mev-boost analytics, by relayscan.io](https://www.relayscan.io/)**
* **[relay list, by ultrasound money](https://relay.ultrasound.money/)**
  
<br>

##### research and code

* **[the role of relays on reorgs, by dataalways (2024)](https://collective.flashbots.net/t/the-role-of-relays-in-reorgs/4247)**
* **[malicious validator $20 from mev bots, by eigenphi (2023)](https://eigenphi.substack.com/p/how-did-a-malicious-validator-steal)**
* **[optimistic relay proposal, by michaelneuder (2023)](https://github.com/michaelneuder/optimistic-relay-documentation/blob/main/proposal.md)**
* **[optimistic relays, by frontier.tech (2023)](https://frontier.tech/optimistic-relays-and-where-to-find-them)**
* **[understanding mev-boost liveness risk, by hasu (2022)](https://writings.flashbots.net/writings/understanding-mev-boost-liveness-risks/)**
* **[keeping relays honest, by yoav (2022)](https://notes.ethereum.org/@yoav/BJeOQ8rI5)**
* **[mev-boost relay code, by flashbots](https://github.com/flashbots/mev-boost-relay)**

