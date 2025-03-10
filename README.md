# 4675hw5
Author: Sabina Sokol

This project demonstrates how to interact with a Hyperledger Fabric network using the Go SDK. The application connects to a Fabric network, initializes the ledger with some assets, performs various transactions such as creating, reading, and transferring assets, and handles errors in a smart contract.

## Prerequisites

### Go Version

This project uses **Go 1.23.0**. Ensure you have this version or a compatible one installed to avoid any version conflicts.

```bash
go version
```

Before running this application, you need to set up the following:

### Install Hyperledger Fabric Test Network
Ensure you have Hyperledger Fabric’s test network set up. This can be done by following the instructions in the [Hyperledger Fabric documentation](https://hyperledger-fabric.readthedocs.io/en/latest/test_network.html).

The application assumes that the test network is available and the Fabric peer is running on `localhost:7051`.

### Dependencies

The project relies on the following Go modules:

- **Hyperledger Fabric Gateway** v1.7.0
- **Fabric Protos Go API** v0.3.4
- **gRPC** v1.67.1
- Other indirect dependencies include libraries for cryptography, networking, protobuf handling, and YAML processing.

Here are the key dependencies:

```go
require (
    github.com/hyperledger/fabric-gateway v1.7.0
    github.com/hyperledger/fabric-protos-go-apiv2 v0.3.4
    google.golang.org/grpc v1.67.1
)

require (
    github.com/miekg/pkcs11 v1.1.1 // indirect
    golang.org/x/crypto v0.28.0 // indirect
    golang.org/x/net v0.28.0 // indirect
    golang.org/x/sys v0.26.0 // indirect
    golang.org/x/text v0.19.0 // indirect
    google.golang.org/genproto/googleapis/rpc v0.0.0-20240814211410-ddb44dafa142 // indirect
    google.golang.org/protobuf v1.35.1 // indirect
)
```

### Installing Dependencies

To install all dependencies, run the following:

```bash
go mod tidy
```

This will automatically download and clean up the required dependencies as specified in the `go.mod` file.

### Fabric Network Configuration
Update the following paths in the `main.go` file to match your local Fabric network configuration:

- **cryptoPath**: Path to the organization’s crypto material.
- **certPath**: Path to the certificate directory of the user (`User1@org1.example.com`).
- **keyPath**: Path to the private key directory for the user.
- **tlsCertPath**: Path to the TLS certificate for the peer.
- **peerEndpoint**: Address of the Fabric peer node (`localhost:7051` by default).
- **gatewayPeer**: The name of the peer in the network (`peer0.org1.example.com` by default).

### 4. Set Chaincode and Channel Names (Optional)
The application connects to the default chaincode (`basic`) and channel (`mychannel`). You can modify these by setting the environment variables:

```bash
export CHAINCODE_NAME="your-chaincode-name"
export CHANNEL_NAME="your-channel-name"
```

## Running the Application

Once you’ve set up the network and installed the dependencies, you can run the application:

```bash
go run webGatewayVerification.go
```

### Overview of Transactions

1. **InitLedger**: Initializes the ledger with a predefined set of assets.
2. **GetAllAssets**: Retrieves all the assets currently stored on the ledger.
3. **CreateAsset**: Creates a new asset with a specified ID, color, size, owner, and appraised value.
4. **ReadAsset**: Reads an asset by its ID from the ledger.
5. **TransferAsset**: Transfers ownership of an asset asynchronously.
6. **Error Handling**: Demonstrates how the application handles errors such as submitting an invalid transaction.

## Error Handling

The application includes an example of handling errors returned by the Fabric peer, such as invalid arguments or transaction failures.


