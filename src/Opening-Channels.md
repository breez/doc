# Opening Channels

By default, whenever a user lacks sufficient inbound liquidity to receive a payment, Breez creates a channel on the fly connected to the Breez routing node. 

However, there are several ways in Breez to create channels with other nodes:
* Opening a channel from your own node:
   * Use the **getinfo_ command** by clicking **Preferences > Developers > General** to retrieve the public key of the mobile node on your device.
   * Click on **Preferences > Developers > Peers > connect** to connect to another node. Note: this won't work for Tor nodes, only regular IP.
   * Open a private channel to the Breez mobile node from the interface of the new node using lncli or similar. Make sure Breez is running in the foreground on your phone while opening the channel.
* Using LNURL-Channel (see below).
* Running lncli commands from the **Preferences > Developers** screen.

**Note**: creating channels manually is recommended only for advanced users.

### LNURL-Channel
[LNURL-Channel](https://github.com/btcontract/lnurl-rfc/blob/master/lnurl-channel.md) allows users to use external services, like Bitrefill Thor, LNBIG, and other [LSPs](https://medium.com/breez-technology/introducing-lightning-service-providers-fe9fb1665d5f) to open additional channels simply by scanning a QR code or clicking on a link. In order to use this function, you need to first choose a provider that offers channel-opening services.

**Important note**:
* Channel reserve amounts differ among LSPs. Channel reserve is the minimum amount of funds a channel must contain that won't be accessible without first closing the channel. While Breez sets the channel reserve to a near-dust value of 600 sats on its default channels, other providers will probably use the default setting of 1% of the channel's capacity. This will be reflected in the Breez UI. 
