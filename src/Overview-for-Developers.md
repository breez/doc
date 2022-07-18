# Overview for Developers

The Breez app is comprised of two main layers:
* [Breez Mobile](https://github.com/breez/breezmobile): the UI layer written in Flutter
* [Breez Library](https://github.com/breez/breez): the business logic written in golang. This layer also refers to all Lightning Network dependencies.

### [Breez Library](https://github.com/breez/breez)
The Breez library is implemented in golang and is responsible for the application's business logic, Lightning/on-chain flows, and LND tight integration.
* The library is compiled and packaged using [gobind](https://godoc.org/golang.org/x/mobile/cmd/gomobile), which creates a binding layer (the "binding" package) and a wrapping API in both java and swift that allow it to be invoked from the Android and iOS apps.
* To build the library in Android using go1.13.4 or above, follow [these instructions](https://github.com/breez/breez/blob/master/README.md).
* All the functions/interfaces (APIs) that need to be exposed to the Breez mobile app are contained in [this file](https://github.com/breez/breez/blob/master/bindings/api.go).

### [Breez Mobile](https://github.com/breez/breezmobile)
* A Flutter implementation is responsible for the UI.
* To manage its state and its internal business logic, the app uses the [BLoC pattern](https://www.flutterclutter.dev/flutter/basics/what-is-the-bloc-pattern/2021/2084/), which uses streams.
* UI logic is handled in objects called [BLoCs](https://github.com/breez/breezmobile/tree/master/lib/bloc). Every domain has its own BLoC.
* [Services](https://github.com/breez/breezmobile/tree/master/lib/services) is a directory that contains the implementation for various stateless services that are injected via _injector.dart_ and are to be used  from BLoCs only.

The rest of the code is pure UI, which uses **Sinks** to push data and **Streams** to read data:
* [Widgets](https://github.com/breez/breezmobile/tree/master/lib/widgets) is a generic widgets directory.
* [Routes](https://github.com/breez/breezmobile/tree/master/lib/routes) contains the pages of the app.


Communication (calling functions) between Flutter to golang occurs via [this bridge](https://github.com/breez/breezmobile/blob/master/lib/services/breezlib/breez_bridge.dart). These functions are defined on both layers and protobuf structures, and they are are used as parameters.

### Adding a function to the Breez Library 

#### Define the endpoint in Breez Library (golang):
1. Use protoc version 3.15
2. [Define the protobuf structure in golang](https://github.com/breez/breez/blob/master/data/messages.proto)
3. Compile the proto: `protoc --proto_path=data --go_out=. data/messages.proto`
4. [Add the endpoint to the binding package](https://github.com/breez/breez/blob/master/bindings/api.go)

#### Define the caller in Breez Mobile (flutter):
1. Compile the protobuf files in Flutter: `protoc --dart_out=grpc:lib/services/breezlib/data/ -I<path to messages.proto>`
2. [Add the function in breez_bridge.dart](https://github.com/breez/breezmobile/blob/master/lib/services/breezlib/breez_bridge.dart)

### Your Development Environment
We recommend you [setup a simnet environment](Running-Breez-in-simnet.md) before testing your code on mainnet.
