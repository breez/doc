# What's the deal with the 600-sat reserve?

Prior to version 0.11, Breez required a minimum balance of 600 sats because of [channel reserve](https://link.medium.com/W2dwNuc583). Channel reserve is a mechanism in Lightning that prevents attacks of spamming channel openings and closures.

The default in Lightning is to set a channel reserve at 1% from the channel capacity (e.g. 10k sats for a 1M-sat channel). In Breez's fork of the lnd Lightning implementation, we've enabled [LSPs](https://medium.com/breez-technology/introducing-lightning-service-providers-fe9fb1665d5f) to set their own [channel reserve values](https://github.com/lightningnetwork/lnd/pull/2708). Breez sets the value to 600 sats, which is a minimal, near-dust value.

These 600 sats are yours. When a user closes a Breez channel (via the **Preferences > Developers** screen), those sats are typically reimbursed. However, closing the channel and redeeming the funds will cost you **_a lot_** more than 600 sats in on-chain fees. Also, we advise against closing the channels with miniscule balances. The funds might become trapped in limbo because they are insufficient for an on-chain transaction and, thus, will not be swept. 
