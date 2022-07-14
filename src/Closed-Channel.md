# Closed Channel

Payment channels on Lightning can be closed without the user actively closing them. This can happen, for instance, when a peer force-closes a channel. Unilateral force closures can result from, say, nodes on the network that hold funds rather than forwarding them, and the Breez LSP may close your channel after a period of inactivity (at least 45 days without executing a Lightning transaction). Furthermore, there are still bugs in [lnd](https://github.com/LightningNetwork/lnd) (the Lightning Network implementation Breez uses) that can cause inadvertent channel closures.

However, users never lose control of their funds (provided they are above dust value) even in the case of force closures. When a channel is closed, the funds are swept to an on-chain address. Typically, it takes 144 blocks (about 24 hours) before the funds from the closed channel appear in a user's local wallet. Once the funds appear in the user's local wallet, Breez displays an interface that allows the user to redeem them, and a warning icon will appear in the top right of the home screen. If no warning icon is displayed, it probably means that the process is still underway.

For more information regarding the closing process:
1. The **Closed Channel** transaction in the payments list should display a detailed status. Please wait 144 confirmations (about 24 hours) after the initial closed channel transaction, at which point the second, sweep transaction (i.e. the transfer from the closed channel to the local Breez wallet) should be displayed. 
2. Consult the output of the _pendingchannels_ command by clicking **Preferences > Developers > Channels > pendingchannels**. 

### 'Pending Closed Channel' seems stuck for a few days

Sometimes on-chain synchronization issues cause the sweep transaction to fail, and the process of closing a channel gets "stuck" at pending. To resolve this issue, please try the following:
1. Click the **Refresh Information** button in the Pending Closed Channel dialog.
2. Click 'Exit Breez'.
3. Reopen Breez and keep the app running in the foreground for at least 15 minutes and prevent the device from going into sleep mode.

This process should re-synchronize your channel and broadcast the sweep transaction, which will enable you to redeem your funds. If that doesn't help, please contact our support: [contact@breez.technology](contact@breez.technology).
