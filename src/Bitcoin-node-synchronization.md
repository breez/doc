# Bitcoin Node Synchronization

By default, Breez uses the following node to connect to the Bitcoin network:

<code>bb1.breez.technology</code>

However, any Bitcoin node that supports block filters (BIP 157) can be used.
[This site](https://bitnodes.io/nodes/?q=NODE_COMPACT_FILTERS) lists alternative nodes. 

### My sync is stuck at 0%, what can I do?
If your node isn't syncing to the network, try the following steps:
* Reset the Bitcoin node by clicking **Preferences > Network > Reset**. 
* Disconnect any VPN or other intermediary software that might be interfering with network traffic.
* Try syncing with a different node listed [here](https://bitnodes.io/nodes/?q=NODE_COMPACT_FILTERS) and entering it in the **Preferences > Network** screen. Choose a regular IP address, not a Tor (.onion) address. 
