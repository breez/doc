### Sending Lightning Payments
Routing fees are dynamic based on the available path. The Breez node has 1 sat base fee in many cases, but some channels have higher fees depending on the liquidity state of the network.
### Receiving LN payments 
No fees, unless a new channel is required.
### Channel creation (setup fee)
0.4% of the amount received, 2000 sats minimum. For more information, see [Channel creation on the fly](https://medium.com/breez-technology/the-breez-release-candidate-getting-lightning-ready-for-the-global-takeover-b5d1f9756229). Currently, Breez adds 100k sats of inbound liquidity to the received amount. For example, if you receive 50k sats, and a new channel is required, Breez will create a 150k channel on-the-fly.

Please note that if this fee is required, it will be displayed in the product. For Lightning transactions, in the 'Receive via Invoice' screen and again under the invoice QR code and for on-chain transactions, under the address QR code in the 'Receive via BTC Address' screen.

There are no additional fees if you keep using the created channels.
### Receive via BTC Address
Send to BTC address is a trustless [submarine swap](Adding-Funds-via-Submarine-Swaps.md). Check the limits below the QR code before sending funds.

No fees, unless a new channel is required.
### Send via BTC Address
Send to BTC address is a trustless [reverse swap](https://medium.com/breez-technology/reverse-submarine-swaps-another-step-towards-a-p2p-lightning-economy-bacb040fdca7). You can send on-chain above 50k sats.

0.5% [Boltz](https://boltz.exchange/) service fee (this is a [trustless swap](https://medium.com/breez-technology/reverse-submarine-swaps-another-step-towards-a-p2p-lightning-economy-bacb040fdca7)) and a dynamic fee based on the current bitcoin mempool usage.
### Streaming sats to Podcasts
No more than 5%.