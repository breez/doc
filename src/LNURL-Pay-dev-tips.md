If you're interested in the [LNURL-Pay bounty](Bounties.md#lnurl-pay-support), you're in the right place. Before diving into this specific feature, please read our [[Overview for Developers]].

Breez already supports various LNURLs, such as auth, withdraw and channel.
Breez Library (golang) exposes an endpoint that [handles lnurl links](https://github.com/breez/breez/blob/master/bindings/api.go#L770).
This endpoint parses the lnurl, handles the initial request (if needed) and sends the response to Breez Mobile (flutter).
Then, Breez Mobile receives the response and prompts the user with the specific UI. Afterwards, it calls the specific function for the next step of the specific lnurl (e.g. FinishLNURLAuth, WithdrawLnurl) which is declared in api.go.

As an example, let's review the LNURL-Auth flow:

#### In Breez Library
1. After parsing the lnurl, the code returns a specific lnurl auth response [here](https://github.com/breez/breez/blob/57527b5a49fcab9f15d90393435df928c2bdfe5e/account/lnurl.go#L41). This response consists of the information that needs to be prompted to the user (such as service host).
2. [FinishLNURLAuth function is implemented](https://github.com/breez/breez/blob/57527b5a49fcab9f15d90393435df928c2bdfe5e/account/lnurl.go#L87) to be used after the user approves the prompt.

#### In Breez Mobile
1. The code in [this file](https://github.com/breez/breezmobile/blob/master/lib/handlers/lnurl_handler.dart) handles lnurl links (whether clicked or scanned). These links automatically sent to Breez library for parsing and receiving an initial response. [This file]((https://github.com/breez/breezmobile/blob/master/lib/handlers/lnurl_handler.dart#L43)) handles the streamed results. 
2. One class [handles the specific Auth results](https://github.com/breez/breezmobile/blob/master/lib/handlers/lnurl_handler.dart#L55), prompts the user, and upon user approval, submits the Login action (that eventually invokes the FinishLNURLAuth in Breez Library).

Similarly, to add support for LNURL-Pay, we need to:
1. Add support for parsing lnurl pay [here](https://github.com/breez/breez/blob/57527b5a49fcab9f15d90393435df928c2bdfe5e/account/lnurl.go).
2. Add handling for prompting the user [here](https://github.com/breez/breezmobile/blob/master/lib/handlers/lnurl_handler.dart).
3. Once the user selects the enters an amount (and maybe other parameters), the flutter code should invoke a golang endpoint to complete the LNURL-Pay logic (invoke a callback to get a payment request and process it).
