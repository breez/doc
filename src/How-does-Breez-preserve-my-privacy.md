# How does Breez preserve my privacy?

Breez uses client-side block filters (Neutrino) for [on-chain monitoring](Introducing-Breez.md#on-chain-monitoring).
So private information like wallet balance is not leaked to third-parties.

Lightning payment path finding is done on the Breez client itself.
So the LSP does not know the payment destination or amount.
