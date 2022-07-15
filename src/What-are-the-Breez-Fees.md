# What fees are there in Breez?

### Sending Lightning Payments
Routing fees depend on the available path. The Breez node charges a base fee of 1 sat in many cases, but fees for some channels are higher depending on the distribution of liquidity throughout the network. Users can limit fees either as a flat maximum or as a percentage of the transaction amount by clicking **Preferences > Lightning Fees** and entering the values desired. 

Please note, however, that limiting fees may cause payments to fail.
### Receiving LN payments 
Receiving a Lightning payment in Breez incurs no fees unless a new channel is required.
### Channel creation 
When a new channel is required to accommodate an incoming payment, Breez charges 0.4% of the amount received, with a minumum of 2000 sats. For more information, see the _Channel creation on the fly_ section of [this blog post](https://medium.com/breez-technology/the-breez-release-candidate-getting-lightning-ready-for-the-global-takeover-b5d1f9756229). 

Currently, Breez adds 100k sats of inbound liquidity to the amount received in an incoming payment. For example, if you receive 50k sats, and a new channel is required, Breez will create a new channel on the fly with a capacity of 150k sats.

Please note that the app displays a notification when a new channel is required and a setup fee will be incurred. For Lightning transactions, the notification will appear in the _Receive via Invoice_ screen and again under the invoice QR code. For on-chain transactions, it will apppear under the address QR code in the _Receive via BTC Address_ screen.

There are no additional fees to continue using the channels created.
### Receiving from a BTC Address
Receiving from BTC address involves a trustless [submarine swap](Adding-Funds-via-Submarine-Swaps.md). Check the limits below the QR code before sending funds.

No additional fees are incurred unless a new channel is required.
### Send to a BTC Address
Sending to a BTC address involves a trustless [reverse swap](https://medium.com/breez-technology/reverse-submarine-swaps-another-step-towards-a-p2p-lightning-economy-bacb040fdca7). Reverse swaps require a minimum transaction amount of 50k sats.

Further, [Boltz](https://boltz.exchange/), the reverse swap provider, charges a fixed service fee of 0.5% and a variable fee based on the current bitcoin mempool usage.
### Streaming sats to podcasts
Breez charges no more than 5% of the sats listeners stream to creators.
