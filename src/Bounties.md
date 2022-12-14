# Bounties

## Active Bounties

Breez is offering bounties for the tasks listed below. Relevant PRs must be reviewed and merged before developers can claim the bounty listed. To inquire about status of a bounty, to contribute to a bounty, or to propose a new bounty, [please send us an email](mailto:contact@breez.technology). 

Please read the [Overview for Developers](https://doc.breez.technology/Overview-for-Developers.html) before getting started. 

### SATSCARD Integration
* The main two interactions are initializing the card and unsealing the card slots for sweeping WIFs. Here is an implementation of the [NFC protocol to talk to the cards in Python](https://github.com/coinkite/coinkite-tap-proto). Nunchuk re-wrote it in C++ [here](https://github.com/nunchuk-io/tap-protocol) and [this](https://github.com/bithyve/cktap-protocol-react-native) is a React Native implementation.
* From a product standpoint, when tapping the card on the device, Breez should show a dialog displaying the card balance and offer a sweep action to a Breez address.
* For anyone interested in the work and testing, the Coinkite team are happy to send test cards.

**Payout**: 5M sats (donated by the Coinkite team) for a complete iOS and Android implementations.

## Developer resources
* [Overview for Developers](Overview-for-Developers.md)
