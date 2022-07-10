# Connecting to a Bitcoin Node

Breez can be connected to any Bitcoin node supporting [BIP 157](https://github.com/bitcoin/bips/blob/master/bip-0157.mediawiki). Bitcoin Core supports BIP 157 starting from v0.21. You can also use btcd. Tor isn't yet supported.

The following configuration flags needs to be added to bitcoin.conf:
```
blockfilterindex=1
peerblockfilters=1
```
