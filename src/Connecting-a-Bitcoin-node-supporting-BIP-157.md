# Connecting to a Bitcoin Node

Breez can be connected to any Bitcoin node that supports [BIP 157](https://github.com/bitcoin/bips/blob/master/bip-0157.mediawiki). Bitcoin Core has supported BIP 157 since v0.21. The btcd implementation is also supported, but Tor is not yet supported.

The following configuration flags needs to be added to bitcoin.conf:
```
blockfilterindex=1
peerblockfilters=1
```
