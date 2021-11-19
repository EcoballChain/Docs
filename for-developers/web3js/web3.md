# Web3

This is the main \(or ‘umbrella’\) class of the web3.js library.

```text
var Web3 = require('web3');​> Web3.utils> Web3.version> Web3.givenProvider> Web3.providers> Web3.modules
```

## Web3.modules[¶](web3.md#web3-modules)​ <a id="web-3-modules"></a>

Will return an object with the classes of all major sub modules, to be able to instantiate them manually.

### Returns[¶](web3.md#returns)​ <a id="returns"></a>

`Object`: A list of module constructors:

* `Eth` - `Constructor`: The Eth module for interacting with the Ethereum network \([web3.eth](web3.eth.md#eth)\).
* `Net` - `Constructor`: The Net module for interacting with network properties \([web3.eth.net](https://web3js.readthedocs.io/en/v1.5.2/web3-eth-net.html#eth-net)\).
* `Personal` - `Constructor`: The Personal module for interacting with the Ethereum accounts \(web3.eth.personal\).
* `Shh` - `Constructor`: The Shh module for interacting with the whisper protocol \([web3.shh](https://docs-depredated.ecoball.org/development/web3js/web3.shh#shh)\).
* `Bzz` - `Constructor`: The Bzz module for interacting with the swarm network \([web3.bzz](https://docs-depredated.ecoball.org/development/web3js/web3.bzz#bzz)\).

### Example[¶](web3.md#example)​ <a id="example"></a>

```text
Web3.modules> {    Eth: Eth(provider),    Net: Net(provider),    Personal: Personal(provider),    Shh: Shh(provider),    Bzz: Bzz(provider),}
```

## Web3 Instance[¶](web3.md#web3-instance)​ <a id="web3-instance"></a>

The Web3 class is an umbrella package to house all Ethereum related modules.

```text
var Web3 = require('web3');​// "Web3.providers.givenProvider" will be set if in an Ethereum supported browser.var web3 = new Web3(Web3.givenProvider || 'ws://some.local-or-remote.node:8546');​> web3.eth> web3.shh> web3.bzz> web3.utils> web3.version
```

## version[¶](web3.md#version)​ <a id="version"></a>

Static accessible property of the Web3 class and property of the instance as well.

Contains the current package version of the web3.js library.

### Returns[¶](web3.md#id1)​ <a id="returns-1"></a>

`String`: The current version.

## utils[¶](web3.md#utils)​ <a id="utils"></a>

Static accessible property of the Web3 class and property of the instance as well.

Utility functions are also exposes on the `Web3` class object directly.

See [web3.utils](https://docs-depredated.ecoball.org/development/web3js/web3.utils#utils) for more.

## setProvider[¶](web3.md#setprovider)​ <a id="setprovider"></a>

```text
web3.setProvider(myProvider)web3.eth.setProvider(myProvider)web3.shh.setProvider(myProvider)web3.bzz.setProvider(myProvider)...
```

Will change the provider for its module.

Note

When called on the umbrella package `web3` it will also set the provider for all sub modules `web3.eth`, `web3.shh`, etc. EXCEPT `web3.bzz` which needs a separate provider at all times.

### Parameters[¶](web3.md#parameters)​ <a id="parameters"></a>

1. `Object` - `myProvider`: a valid provider.

### Example: Local Geth Node[¶](web3.md#example-local-geth-node)​ <a id="example-local-geth-node"></a>

```text
var Web3 = require('web3');var web3 = new Web3('http://localhost:8545');// orvar web3 = new Web3(new Web3.providers.HttpProvider('http://localhost:8545'));​// change providerweb3.setProvider('ws://localhost:8546');// orweb3.setProvider(new Web3.providers.WebsocketProvider('ws://localhost:8546'));​// Using the IPC provider in node.jsvar net = require('net');var web3 = new Web3('/Users/myuser/Library/Ethereum/geth.ipc', net); // mac os path// orvar web3 = new Web3(new Web3.providers.IpcProvider('/Users/myuser/Library/Ethereum/geth.ipc', net)); // mac os path// on windows the path is: "\\\\.\\pipe\\geth.ipc"// on linux the path is: "/users/myuser/.ethereum/geth.ipc"
```

### Example: Remote Node Provider[¶](web3.md#example-remote-node-provider)​ <a id="example-remote-node-provider"></a>

```text
// Using a remote node provider, like Alchemy (https://www.alchemyapi.io/supernode), is simple.var Web3 = require('web3');var web3 = new Web3("https://eth-mainnet.alchemyapi.io/v2/your-api-key");
```

## providers[¶](web3.md#providers)​ <a id="providers"></a>

```text
web3.providersweb3.eth.providersweb3.shh.providersweb3.bzz.providers...
```

Contains the current available providers.

### Value[¶](web3.md#value)​ <a id="value"></a>

`Object` with the following providers:

> * `Object` - `HttpProvider`: HTTP provider, does not support subscriptions.
> * `Object` - `WebsocketProvider`: The Websocket provider is the standard for usage in legacy browsers.
> * `Object` - `IpcProvider`: The IPC provider is used node.js dapps when running a local node. Gives the most secure connection.

### Example[¶](web3.md#id4)​ <a id="example-1"></a>

```text
var Web3 = require('web3');// use the given Provider, e.g in Mist, or instantiate a new websocket providervar web3 = new Web3(Web3.givenProvider || 'ws://remotenode.com:8546');// orvar web3 = new Web3(Web3.givenProvider || new Web3.providers.WebsocketProvider('ws://remotenode.com:8546'));​// Using the IPC provider in node.jsvar net = require('net');​var web3 = new Web3('/Users/myuser/Library/Ethereum/geth.ipc', net); // mac os path// orvar web3 = new Web3(new Web3.providers.IpcProvider('/Users/myuser/Library/Ethereum/geth.ipc', net)); // mac os path// on windows the path is: "\\\\.\\pipe\\geth.ipc"// on linux the path is: "/users/myuser/.ethereum/geth.ipc"
```

### Configuration[¶](web3.md#configuration)​ <a id="configuration"></a>

```text
// ====// Http// ====​var Web3HttpProvider = require('web3-providers-http');​var options = {    keepAlive: true,    withCredentials: false,    timeout: 20000, // ms    headers: [        {            name: 'Access-Control-Allow-Origin',            value: '*'        },        {            ...        }    ],    agent: {        http: http.Agent(...),        baseUrl: ''    }};​var provider = new Web3HttpProvider('http://localhost:8545', options);​// ==========// Websockets// ==========​var Web3WsProvider = require('web3-providers-ws');​var options = {    timeout: 30000, // ms​    // Useful for credentialed urls, e.g: ws://username:[email protected]:8546    headers: {      authorization: 'Basic username:password'    },​    clientConfig: {      // Useful if requests are large      maxReceivedFrameSize: 100000000,   // bytes - default: 1MiB      maxReceivedMessageSize: 100000000, // bytes - default: 8MiB​      // Useful to keep a connection alive      keepalive: true,      keepaliveInterval: 60000 // ms    },​    // Enable auto reconnection    reconnect: {        auto: true,        delay: 5000, // ms        maxAttempts: 5,        onTimeout: false    }};​var ws = new Web3WsProvider('ws://localhost:8546', options);
```

More information for the Http and Websocket provider modules can be found here:

> ​

## givenProvider[¶](web3.md#givenprovider)​ <a id="givenprovider"></a>

```text
web3.givenProviderweb3.eth.givenProviderweb3.shh.givenProviderweb3.bzz.givenProvider...
```

When using web3.js in an Ethereum compatible browser, it will set with the current native provider by that browser. Will return the given provider by the \(browser\) environment, otherwise `null`.

### Returns[¶](web3.md#id5)​ <a id="returns-2"></a>

`Object`: The given provider set or `null`;

## currentProvider[¶](web3.md#currentprovider)​ <a id="currentprovider"></a>

```text
web3.currentProviderweb3.eth.currentProviderweb3.shh.currentProviderweb3.bzz.currentProvider...
```

Will return the current provider, otherwise `null`.

### Returns[¶](web3.md#id7)​ <a id="returns-3"></a>

`Object`: The current provider set or `null`.

## BatchRequest[¶](web3.md#batchrequest)​ <a id="batchrequest"></a>

```text
new web3.BatchRequest()new web3.eth.BatchRequest()new web3.shh.BatchRequest()new web3.bzz.BatchRequest()
```

Class to create and execute batch requests.

### Returns[¶](web3.md#id10)​ <a id="returns-4"></a>

`Object`: With the following methods:

> * `add(request)`: To add a request object to the batch call.
> * `execute()`: Will execute the batch request.

### Example[¶](web3.md#id11)​ <a id="example-2"></a>

```text
var contract = new web3.eth.Contract(abi, address);​var batch = new web3.BatchRequest();batch.add(web3.eth.getBalance.request('0x0000000000000000000000000000000000000000', 'latest', callback));batch.add(contract.methods.balance(address).call.request({from: '0x0000000000000000000000000000000000000000'}, callback2));batch.execute();
```

## extend[¶](web3.md#extend)​ <a id="extend"></a>

```text
web3.extend(methods)web3.eth.extend(methods)web3.shh.extend(methods)web3.bzz.extend(methods)...
```

Allows extending the web3 modules.

Note

You also have `*.extend.formatters` as additional formatter functions to be used for input and output formatting. Please see the [source file](https://github.com/ethereum/web3.js/blob/1.x/packages/web3-core-helpers/src/formatters.js) for function details.

### Parameters[¶](web3.md#id12)​ <a id="parameters-1"></a>

1. `methods` - `Object`: Extension object with array of methods description objects as follows:
   * `property` - `String`: \(optional\) The name of the property to add to the module. If no property is set it will be added to the module directly.
   * `methods` - `Array`: The array of method descriptions:
     * `name` - `String`: Name of the method to add.
     * `call` - `String`: The RPC method name.
     * `params` - `Number`: \(optional\) The number of parameters for that function. Default 0.
     * `inputFormatter` - `Array`: \(optional\) Array of inputformatter functions. Each array item responds to a function parameter, so if you want some parameters not to be formatted, add a `null` instead.
     * ```outputFormatter - ``Function```: \(optional\) Can be used to format the output of the method.

### Returns[¶](web3.md#id13)​ <a id="returns-5"></a>

`Object`: The extended module.

### Example[¶](web3.md#id14)​ <a id="example-3"></a>

```text
web3.extend({    property: 'myModule',    methods: [{        name: 'getBalance',        call: 'eth_getBalance',        params: 2,        inputFormatter: [web3.extend.formatters.inputAddressFormatter, web3.extend.formatters.inputDefaultBlockNumberFormatter],        outputFormatter: web3.utils.hexToNumberString    },{        name: 'getGasPriceSuperFunction',        call: 'eth_gasPriceSuper',        params: 2,        inputFormatter: [null, web3.utils.numberToHex]    }]});​web3.extend({    methods: [{        name: 'directCall',        call: 'eth_callForFun',    }]});​console.log(web3);> Web3 {    myModule: {        getBalance: function(){},        getGasPriceSuperFunction: function(){}    },    directCall: function(){},    eth: Eth {...},    bzz: Bzz {...},    ...}
```

