The Breez app is comprised of two main layers:
* [Breez Mobile](https://github.com/breez/breezmobile): UI layer written in Flutter
* [Breez Library](https://github.com/breez/breez): business logic written in golang. This layer also refers to all lightning network dependencies.

### [Breez Library](https://github.com/breez/breez)
Implemented in golang and responsible for the application business logic, lightning/on-chain flows and LND tight integration.
* Compiled and packaged into a library using [gobind](https://godoc.org/golang.org/x/mobile/cmd/gomobile) which creates a binding layer (the "binding" package) and wrapping API in both java and swift that makes it possible to be invoked from the android and iOS apps.
* To build the library in android using go1.13.4 or above follow [these instructions](https://github.com/breez/breez/blob/master/README.md).
* In general, all the functions/interfaces (APIs) that need to be exposed to the Breez mobile app exist in [this file](https://github.com/breez/breez/blob/master/bindings/api.go).

### [Breez Mobile](https://github.com/breez/breezmobile)
* Implemented in flutter and responsible for the app UI.
* For managing its state and its internal business logic, the app uses the bloc pattern which uses streams.
* UI logic is handled in objects called [Blocs](https://github.com/breez/breezmobile/tree/master/lib/bloc). Every domain has its own bloc.
* [Services](https://github.com/breez/breezmobile/tree/master/lib/services) is a directory that contains the implementation for various stateless services that are injected via _injector.dart_ and to be used only from blocs.

The rest of the code is pure UI which uses **Sinks** to push data and **Streams** to read data:
* [Widgets](https://github.com/breez/breezmobile/tree/master/lib/widgets) is a generic widgets directory.
* [Routes](https://github.com/breez/breezmobile/tree/master/lib/routes) contains the pages of the app.


Communicating (calling functions) between flutter to golang is done via [this bridge](https://github.com/breez/breezmobile/blob/master/lib/services/breezlib/breez_bridge.dart). These functions there are defined on both layers and protobuf structures are used as parameters.

### Adding a function in Breez Library 

#### Define the endpoint in Breez Library (golang):
1. Use protoc version 3.15
2. [Define the protobuf structure in golang](https://github.com/breez/breez/blob/master/data/messages.proto)
3. Compile the proto: `protoc --proto_path=data --go_out=. data/messages.proto`
4. [Add the endpoint to the binding package](https://github.com/breez/breez/blob/master/bindings/api.go)

#### Define the caller in Breez Mobile (flutter):
1. Compile the protobuf files in flutter: `protoc --dart_out=grpc:lib/services/breezlib/data/ -I<path to messages.proto>`
2. [Add the function in breez_bridge.dart](https://github.com/breez/breezmobile/blob/master/lib/services/breezlib/breez_bridge.dart)

### Your Development Environment
We recommend you [setup a simnet environment](Running-Breez-in-simnet.md) before testing your code on mainnet.
