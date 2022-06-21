When adding funds via a BTC address, Breez uses something called [Submarine Swaps](https://www.google.com/amp/s/blog.muun.com/a-closer-look-at-submarine-swaps-in-the-lightning-network/amp/): it's a script address that guarantees that the funds in the provided address can be spent only if a Lightning tx is executed to the user's node within 288 blocks (~48 hours). If a Lightning tx isn't executed in this timeframe, the user is allowed to redeem the funds, but only after the time lock expires.

_Note for advanced users_: The Submarine Swaps script can be exported from Breez by long-click on the QR code of the address.

### Why does Breez use Submarine Swaps?
Submarine Swaps allows Breez to support on-chain transactions while maintaining a single balance. Meaning, all of the users funds are in their Lightning nodes and there's no need to maintain a BTC wallet functionality which simplifies the user experience.

### Limitations
* Sending more funds than the specified limit (shown in Breez below the address) will trigger a refund since the Submarine Swaps process is bounded by the Lightning channel capacity. 
* Sending a small amount to a Submarine Swaps address may trigger a refund. The reason is that if Breez can't guarantee to execute a confirmed on-chain tx within the time lock timeframe, users can spend the funds even if Breez has already executed a Lightning tx. 
* Sending multiple tx to the same address will trigger a refund. Only the first tx is processed and will be transferred to user's balance.

### How to get a refund?
You will see a 'Get Refund' action in the Breez side-menu once the funds are ready to be redeemed (~48h after the on-chain tx is confirmed). You will be asked to entered a BTC address. The funds will be sent from the Submarine Swaps address to the destination address you enter. 