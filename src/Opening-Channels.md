# Openning Channels

By default, Breez creates channels on the fly from the Breez routing node in case you don't have enough inbound liquidity to receive a payment. 

However, there are several ways to create channels with other nodes in Breez:
* Opening a channel from your own node:
   * Use the _getinfo_ command in the Developers screen to retrieve the mobile node public key.
   * Run _Peers> connect_ from the Developers screen to connect to your own node. Note this won't work for Tor nodes, only regular IP.
   * From your own node, open a **private** (--private) channel with Breez mobile node using lncli or similar. Make sure Breez is in the foreground while opening the channel.
* Using LNURL-Channel (see below).
* Running lncli commands from the Developers screen.

**Note**: creating additional channels is recommended only for advanced users.

## LNURL-Channel
[LNURL-Channel](https://github.com/btcontract/lnurl-rfc/blob/master/lnurl-channel.md) allows users to use external services like Bitrefill Thor, LNBIG, and other [LSPs](https://medium.com/breez-technology/introducing-lightning-service-providers-fe9fb1665d5f) to open additional channels simply by scanning a QR code or clicking on a link. In order to use it, you need to first choose a provider that offers channel opening services.

Important note:
* Each LSP can set a different channel reserve amount. Channel reserve means that there are funds that you won't be able to use without first closing the channel. While Breez sets the channel reserve to a near-dust value of 600 sats on its default channel, other providers will probably use the default setting of 1% of the channel capacity. This will be reflected in the Breez UI. 
