# Basic commands

Curl is a tool you need to test basic commands, and most Linux systems come with .

If the test is performed on a local node machine, the address and port of the node's external service is :[http://127.0.0.1:8545](http://127.0.0.1:8545).

If the deployment is on the public internet and the domain name resolution, you can access through the domain name, such as [http://api.ecoball.org:8545](http://api.ecoball.org:8545).

The first line of each of the following commands is the request execution and the second line is the return response.

#### web3\_clientVersion <a href="#web-3-_clientversion" id="web-3-_clientversion"></a>

Returns the client version number.

curl -H "Content-Type: application/json" -X POST [http://127.0.0.1:8545](http://127.0.0.1:8545) --data '{"jsonrpc":"2.0","method":"web3\_clientVersion","params":\[],"id":67}'

{"jsonrpc":"2.0","result":"EcoBall//v0.9.9-unstable/x86\_64-linux-gnu/rustc1.52.1","id":67}

#### web3\_sha3 <a href="#web-3-_sha3" id="web-3-_sha3"></a>

Returns the keccak-256 of the given value.

curl -H "Content-Type: application/json" -X POST [http://127.0.0.1:8545](http://127.0.0.1:8545) --data '{"jsonrpc":"2.0","method":"web3\_sha3","params":\["0x68656c6c6f20776f726c64"],"id":64}'

{"jsonrpc":"2.0","result":"0x47173285a8d7341e5e972fc677286384f802f8ef42a5ec5f03bbfa254cb01fad","id":64}

#### net\_version <a href="#net_version" id="net_version"></a>

Returns the current network ID.

curl -H "Content-Type: application/json" -X POST [http://127.0.0.1:8545](http://127.0.0.1:8545) --data '{"jsonrpc":"2.0","method":"net\_version","params":\[],"id":67}'

{"jsonrpc":"2.0","result":"100","id":67}

#### net\_listening <a href="#net_listening" id="net_listening"></a>

Returns the client listening network connection status.

curl -H "Content-Type: application/json" -X POST [http://127.0.0.1:8545](http://127.0.0.1:8545) --data '{"jsonrpc":"2.0","method":"net\_listening","params":\[],"id":67}'

{"jsonrpc":"2.0","result":true,"id":67}

#### net\_peerCount <a href="#net_peercount" id="net_peercount"></a>

Returns the number of nodes currently connected to the client.

curl -H "Content-Type: application/json" -X POST [http://127.0.0.1:8545](http://127.0.0.1:8545) --data '{"jsonrpc":"2.0","method":"net\_peerCount","params":\[],"id":74}'

{"jsonrpc":"2.0","result":"0x1","id":74}

#### eth\_protocolVersion <a href="#eth_protocolversion" id="eth_protocolversion"></a>

Returns the current Ethereum protocol version number. Since Ecoball is Ethereum compatible, the protocol version number indicates if the Dapp is suitable for migration.

curl -H "Content-Type: application/json" -X POST [http://127.0.0.1:8545](http://127.0.0.1:8545) --data '{"jsonrpc":"2.0","method":"eth\_protocolVersion","params":\[],"id":67}'

{"jsonrpc":"2.0","result":"65","id":67}

#### eth\_gasPrice <a href="#eth_gasprice" id="eth_gasprice"></a>

Returns the current gas price.

curl -H "Content-Type: application/json" -X POST [http://127.0.0.1:8545](http://127.0.0.1:8545) --data '{"jsonrpc":"2.0","method":"eth\_gasPrice","params":\[],"id":71}'

{"jsonrpc":"2.0","result":"0x0","id":71}

#### eth\_accounts <a href="#eth_accounts" id="eth_accounts"></a>

Returns the wallet address of the current node.

curl -H "Content-Type: application/json" -X POST [http://127.0.0.1:8545](http://127.0.0.1:8545) --data '{"jsonrpc":"2.0","method":"eth\_accounts","params":\[],"id":71}'

{"jsonrpc":"2.0","result":\["0x01c9a1515ae1d0df16e30f48ab5cbddcfd9413d4"],"id":71}

#### eth\_blockNumber <a href="#eth_blocknumber" id="eth_blocknumber"></a>

Returns the current block number.

curl -H "Content-Type: application/json" -X POST [http://127.0.0.1:8545](http://127.0.0.1:8545) --data '{"jsonrpc":"2.0","method":"eth\_blockNumber","params":\[],"id":71}'

{"jsonrpc":"2.0","result":"0xfaf","id":71}

#### eth\_getBalance <a href="#eth_getbalance" id="eth_getbalance"></a>

Returns the balance of the given wallet address.

curl -H "Content-Type: application/json" -X POST [http://127.0.0.1:8545](http://127.0.0.1:8545) --data '{"jsonrpc":"2.0","method":"eth\_getBalance","params":\["0x01c9a1515ae1d0df16e30f48ab5cbddcfd9413d4", "latest"],"id":1}'

{"jsonrpc":"2.0","result":"0xbcec172badbc540000","id":1}

In the JSON object, result is the balance corresponding to the wallet address, the hexadecimal number, which can be converted to base 10, and then divided by 10\*\*18, to get the number of ECO.
