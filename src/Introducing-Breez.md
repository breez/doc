# Introducing Breez Mobile

Breez is a full-service, non-custodial Lightning client. Let’s break that down:

* **Lightning** is a bitcoin payment network that reduces transaction times from minutes to milliseconds and transaction fees from several dollars to a few cents or less. Lightning turns bitcoin from digital gold into digital currency while preserving all of the benefits that make bitcoin great.
* **Non-custodial** means that Breez doesn’t take possession of users’ money. Many Lightning clients do take possession of their users’ money. They’re basically bitcoin banks. With a non-custodial app like Breez, all users are their own banks. Breez uses a forked version of [lnd](https://github.com/LightningNetwork/lnd) and [Neutrino](https://github.com/lightninglabs/neutrino). The Breez app actually runs a full Lightning node under the hood. Advanced users can interact with the underlying Lightning node by invoking [lncli commands](https://dev.lightning.community/overview/) in the _Preferences> Developers_ screen.
* **Full-service** means that Breez takes care of almost all the technical operations automatically and in the background. Things like channel creation, inbound liquidity, and routing stay under the hood. (But Breez is also [open source](https://github.com/breez), so those interested in auditing the technology are welcome to do so!)

Breez includes a [Point-of-Sale mode](How-to-Get-Started-with-Breez-POS.md), which transforms the app from a Lightning wallet into a Lightning cash register with the slide of a finger, allowing everyone to become a merchant and accept Lightning payments. It also includes a [next-generation podcast player](https://medium.com/breez-technology/podcasts-on-breez-streaming-sats-for-streaming-ideas-d9361ae8a627), allowing users to stream sats to their favorite content creators.

Note: the app is still in beta and there is a chance your money will be lost. Only use this app if you are willing to take this risk.

## Features

### No channel management: zero-conf channels are created on the fly

Breez seamlessly opens channels as needed on-the-fly. Here's how it works:

1. When the recipient wants to receive a payment but lacks inbound capacity, their Breez app recognizes the lack and issues two invoices using the same [preimage](https://wiki.ion.radar.tech/tech/bitcoin/pre-image): one invoice is issued to the sender (requesting a payment) and a second is issued to the Breez [LSP](https://medium.com/breez-technology/introducing-lightning-service-providers-fe9fb1665d5f). The amount of the second invoice equals the amount requested from the payer minus a miniscule service fee to Breez for opening the channel the recipient requires. The invoice sent to the sender includes routing instructions, indicating a pseudo-channel between the recipient and the Breez node.
2. When the sender pays the invoice they received from the recipient, the Breez node intercepts the payment and holds it.
3. The Breez LSP then opens a channel with the recipient and skips funding confirmation. Then it pays the recipient the second invoice and receives the preimage.
4. Once the preimage is received from the recipient, Breez settles the payment with the sender.

Breez funds the convenience of zero-conf channel creation by [charging a fee](What-are-the-Breez-Fees.md).

The channels Breez creates on the fly are actually zero-conf channels. These differ from standard channels in that they can function before they’ve been confirmed on the blockchain. Instead of making users wait until blocks are mined, these channels become active instantly, allowing users to spend their funds immediately after receiving them.

### Cloud backup

Like all true Lightning wallets, Breez is a ["hot" wallet](https://dergigi.com/2022/06/27/the-words-we-use-in-bitcoin/) and thus requires frequent cloud backups. To avoid relying on the availability/existence of the Breez server, we offer automatic backups to Google Drive, iCloud, Nextcloud, or any WebDav server. From a security standpoint, there are also many advantages to saving these backups in a major third-party cloud-storage provider. For more information, see our [Backup FAQ](Backup-FAQ.md).

### On-chain transactions

When sending or receiving funds via BTC addresses, Breez uses [Submarine Swaps](https://docs.lightning.engineering/the-lightning-network/lightning-overview/understanding-submarine-swaps), which allow Breez to support on-chain transactions while maintaining a single balance. In other words, all of the users’ funds are in their Lightning channels, which simplifies the user experience by obviating many functions of a standard BTC wallet.

For more information, see:



* [Adding Funds via Submarine Swaps](Adding-Funds-via-Submarine-Swaps.md) (Receive via BTC Address)
* [Reverse Submarine Swaps](https://medium.com/breez-technology/reverse-submarine-swaps-another-step-towards-a-p2p-lightning-economy-bacb040fdca7) (Send via BTC Address)

### On-chain monitoring

Breez uses [Neutrino](https://github.com/lightninglabs/neutrino) to fetch chain information. Neutrino provides [better privacy](https://medium.com/breez-technology/the-only-thing-better-than-minimal-trust-is-none-at-all-34456f650332?source=collection_home---4------8-----------------------) than current alternatives and allows users to connect to their [own Bitcoin nodes](Connecting-a-Bitcoin-node-supporting-BIP-157.md) via the _Preferences > Network_ screen.

Breez includes a background watcher to help users control the state of their channels. This process notifies users of cheating attempts even when the app is closed, helping them to retrieve their money. The refund period is 720 blocks, so users are automatically protected by simply using their phones at least once every 5 days. The Breez app doesn’t even need to be open, since the watcher runs periodically in the background without any further demands on the user.

### Connecting to multiple nodes

By default, Breez creates channels on the fly with the Breez LSP whenever users lack the inbound liquidity to receive a payment. There are, however, several ways to create channels with other nodes in Breez: users can open a channel to their own node, use LNURL-Channel, or run lncli commands from the Developers screen. For more information, [see here](Opening-Channels.md).

### Point-of-Sale

Breez works like a digital cash register for brick-and-mortar businesses and merchants who want to accept Lightning payments. It includes features and a user interface tailored to merchants’ needs, like manager passwords, a catalog of items, fiat display, and the ability to export transaction information. [Read this to get started with Breez POS](How-to-Get-Started-with-Breez-POS.md).

### Podcast player

Breez comes with a built-in, next-generation podcast player: users can find and subscribe to podcasts, stream payments while listening, and send real-time tips to applaud their favorite creators at their favorite moments. While listening, users can set a rate of how many sats per minute to stream back to the creators. For example, to pay 3000 sats for an hour-long episode, the user would set the rate to 50 sats/min. Setting the rate to 0 lets the user listen for free. Users can also send one-off tips to the creators by pressing the Boost! button and attach a direct message to the podcasters (aka Boostagrams). 

For more information about Breez support of Podcating 2.0, [read this article](https://medium.com/breez-technology/podcasts-on-breez-streaming-sats-for-streaming-ideas-d9361ae8a627). To see streaming sats and boosts in action, [check out this video](https://youtu.be/wA3Qn7vhY7Y?t=474).

Breez includes many more features, like full LNURL support, private mode, payment filters, Connect to Pay, biometric login, fast graph sync, scanning QR code from an image, fiat currencies and Lightning addresses. To learn more, please take a look at [our medium publication](https://medium.com/breez-technology), [GitHub projects](https://github.com/breez), or follow us on [Twitter](https://twitter.com/breez_tech).

To learn more about Breez, please check out our [site](https://breez.technology) and our [Medium publication](https://medium.com/breez-technology).
