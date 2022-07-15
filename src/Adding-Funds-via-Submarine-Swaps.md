# Adding Funds via Submarine Swaps

[Submarine swaps](https://www.google.com/amp/s/blog.muun.com/a-closer-look-at-submarine-swaps-in-the-lightning-network/amp/) allow users to transfer on-chain funds to Lightning without trust or counterparty risk, which is exactly how Breez uses them. 

Submarine swaps are designed such that the funds in the address provided can only be spent if a Lightning transaction is executed to the user's node within 288 blocks (about 48 hours). If no Lightning transaction is executed by this deadline, the user can redeem the funds when the time lock expires.

**Note for advanced users**: The script for a submarine swap can be exported from Breez by long-clicking the QR code of the address.

### Why does Breez use Submarine Swaps?
Submarine swaps allow Breez to support on-chain transactions while maintaining a single balance. In other words, all of the users' funds are on their Lightning nodes, so there's no need to maintain a separate BTC wallet within Breez, which greatly simplifies the user experience.

### Limitations
* Sending more funds than the specified limit (shown in Breez below the address) will trigger a refund since no submarine swap may exceed the recipient's channel capacity. 
* Sending a small amount to a submarine swap address may trigger a refund because users could theoretically spend the funds even if Breez has already executed a Lightning transaction. The reason is that Breez cannot always ensure the on-chain transaction is confirmed before the time lock expires. 
* Sending multiple transactions in quick succession to the same address will trigger a refund. Each transaction must be completed and transferred to the user's balance before the next can be initiated.

### How can users claim their refunds?
Once the funds are ready to be redeemed (about 48 hours after the on-chain transaction has been confirmed), a **Get Refund** option will appear in the Breez side-menu. Click on it and enter an on-chain BTC address when prompted. The funds will be sent to the address entered. 
