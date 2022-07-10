# Closed Channel

In Lightning Network, your channel can get closed, even you didn't actively closed it (e.g. force-closed by your peer). This can happen due to bad behaviour of nodes in the network (holding funds w/o settling them), or the Breez LSP may close your channel after a period of inactivity (at least 45 days without executing Lightning transactions). Furthermore, there are still issues (bugs) in lnd (the Lightning Network implementation Breez uses) that may cause your channel to get closed.

However, even in this case, you are still in full control of your funds (if they amount is above dust value). When a channel get closed, your funds are sent to the block hain. Typically it takes 144 blocks to send your funds from the closed channel to your a local wallet (aka sweep transaction). After the second tx is confirmed (from the closed channel tx to your local wallet), Breez displays an interface that allows you to redeem them. You should see a warning icon on top right corner of its home screen. If no warning icon is displayed, it probably means the closing process wasn't yet completed.
To get more information regarding the closing process:
1. Click on the **Closed Channel** transaction in the payments list should display a detailed status. Please wait for 144 confirmations (~24h) for the initial closed channel transaction. After the initial tx, another tx should be displayed. This is a sweep tx (from the closed channel to a local wallet in Breez).
2. View the output of the _Channels > pendingchannels_ command from the _Advanced> Developers_ screen. 

### Status is 'Pending Closed Channel' for a few days

Sometimes, due to issues regrading on-chain synchronization, the sweep transaction isn't executed and the channel closing process is "stuck" at pending. In order to resolve it, please try the following:
1. Click the 'Refresh Information' button in the Pending Closed Channel dialog.
2. Click 'Exit Breez'.
3. Reopen Breez and keep in the foreground for at least 15min. Make sure the device isn't going to sleep mode.

This process should re-sync your channel and broadcast the sweep transaction that will enable you to redeem your funds. If that doesn't help, please contact our support: contact@breez.technology.
