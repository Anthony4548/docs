# Makalu PoC-1

## Build your own network and send cross-chain transactions

### 1. Running atlas

See [Become Validator](../map-protocol/setValidator.md)

### 2. Deploy contract to ethereum and atlas
(1). Deploy [USDT](https://github.com/mapprotocol/contracts/blob/884cc2b64ff14c01fa60251851537e2f877a14a2/contracts/Usdt.sol)

(2). Deploy [MapERC20](https://github.com/mapprotocol/contracts/blob/884cc2b64ff14c01fa60251851537e2f877a14a2/contracts/MapERC20.sol)

The constructor of this contract receives 3 parameters namely name, symbol and tokenBinding.
specify name and symbol assign the USDT contract address obtained in the previous step to tokenBinding

(3). Deploy [MapRouter](https://github.com/mapprotocol/contracts/blob/884cc2b64ff14c01fa60251851537e2f877a14a2/contracts/MapRouter.sol)

The constructor of this contract receives 2 parameters, mpcAddress and verify. mpcAddress is the address of the relayer 
that listen and verifies cross-chain transactions. This will be described in detail below. assign the
[TxVerify](../cross-chain/tx-verify/Tx-Verify-Contract.md#contract-address) contract address to verify

(4). Set Authentication

Call the setAuth method of the MapERC20 contract and pass in the address of the MapRouter contract to add
authentication so that the MapRouter contract can call the MapERC20 contract。

### 3. Send cross chain transactions on the ethereum
Call the swapOut method of the MapRouter contract to send a cross chain transaction. The swapOut method receives
four parameters, namely token, to, amount, toChainID. 
token: token contract address, here can be MapERC20 contract address,
to: the address of the recipient of the transaction, 
amount: transaction amount, 
toChainId: the target chain of cross-chain transactions,
see [supported chain list](../cross-chain/light-client-data/Header-Store-API.md#chain-identification-list).

### 4. Register as a relayer and synchronize the block header to atlas
Atlas uses light client verification to verify on-chain transactions on the opposite chain to achieve the purpose of 
cross-chain transaction data (assets). So this requires you to synchronize the block header to atlas to achieve 
cross-chain transaction verification.

For how to register as a relayer and synchronize the block header, please refer to the document linked below.

[How To Become Relayer](../map-protocol/relayer/QuickStart.md)

[Sync Block Header](../cross-chain/light-client-data/Header-Store-Contract.md)

### 5. Listen cross chain transaction events and verify transactions
In this step, you need to implement a simple program to listen cross-chain transaction events on ethereum. 
When cross-chain transactions are monitored, cross-chain transaction verification data needs to be constructed, 
and then the sawpIn method of the MapRouter contract deployed on atlas is mobilized. 
The sawpIn method will call the pre-compiled contract of atlas to verify whether the cross-chain transaction exists and is legal. 
If the verification is passed, the transfer amount will be sent to the recipient of the cross-chain transaction.

[How to construct cross-chain transaction verification data](../cross-chain/tx-verify/Tx-Verify-Contract.md#example)

### 6. Query whether the cross-chain transaction has arrived
After the above steps, you have completed a cross-chain transaction. Now let's verify whether the transaction amount has arrived. 
To check the balance of the account, we can call the balanceOf of the MapERC20 contract deployed on atlas.

## Use our existing network to send cross-chain transactions

#### Atlas  address:

| network  | address | chainid | networkid |
| -------- | ------  | ------ | ------ |
| mainnet  | https://poc2-rpc.maplabs.io | 22776 | 22776 |
| testnet  | http://13.76.138.119:7445   | 212 | 212 |

| comment  | address |
| -------- | ------  |
| 浏览器    | https://makalu.mapscan.io |
| API 接口  | https://makalu-api.mapscan.io |
| PoC-2 RPC| https://poc2-rpc.maplabs.io |
| IPFS     | https://makalu-ipfs.maplabs.io  |
| Graph    | https://makalu-graph.maplabs.io |
| Graph API| https://makalu-graph-api.maplabs.io |

#### Contract address:

| contract| address |
| -------- | ------ |
| Atlas MapRouter | 0xB864eEe844698de06Dd305CBf729fDD765d9592D |
| Ropsten MapRouter | 0xa32620a8c7868fe31154d4c58ab7e7e2e9810e71|

Now that we have deployed a cross-chain transaction contract on Ropsten, you can directly call.
Let's take a look at how to send a cross-chain transaction in Ropsten.

The address of the MapRouter contract on the Ropsten testnet is 0xa32620a8c7868fe31154d4c58ab7e7e2e9810e71. 
Using this address, you can use the remix or Go program to call sawpOut to send cross-chain transactions. 
After sending a cross-chain transaction, you do not need to synchronize block headers, monitor cross-chain events, 
verify cross-chain transactions, etc., just wait for the transaction amount to arrive. 
The premise is that cross-chain transactions exist and are legal.

The Atlas main network address is https://poc2-rpc.maplabs.io, and the address of the MapERC20 contract deployed 
on Atlas is 0xB864eEe844698de06Dd305CBf729fDD765d9592D. Using the above address, you can use the remix or Go program to 
call the balanceOf of the MapERC20 contract to check the balance.

