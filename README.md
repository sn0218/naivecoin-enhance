# Naivecoin

This is the enhanced version of naivecoin. <br />
Merkle root calculation is implemented and the Merkle root hash is added in each block.<br />
The original naivecoin tutorial: https://lhartikk.github.io/ <br />
The original repository  https://github.com/lhartikk/naivecoin/tree/master <br />

### Install
```
npm install
```

### Getting start (set up one node)
```
npm start
```
### Quick start (set up two nodes)
```
HTTP_PORT=3001 P2P_PORT=6001 npm start
HTTP_PORT=3002 P2P_PORT=6002 PEERS=ws://localhost:6001 npm start

```

##  API

##### Get blockchain
```
curl http://localhost:3001/blocks | json_pp
```

##### Mine a block
```
curl -X POST http://localhost:3001/mineBlock | json_pp
``` 

##### Send transaction
```
curl -H "Content-type: application/json" --data '{"address": "04bfcab8722991ae774db48f934ca79cfb7dd991229153b9f732ba5334aafcd8e7266e47076996b55a14bf9913ee3145ce0cfc1372ada8ada74bd287450313534b", "amount" : 10' http://localhost:3001/sendTransaction | json_pp
```

##### Query transaction pool
```
curl http://localhost:3001/transactionPool | json_pp
```

##### Mine transaction

```
curl -H "Content-type: application/json" --data '{"address": "04bfcab8722991ae774db48f934ca79cfb7dd991229153b9f732ba5334aafcd8e7266e47076996b55a14bf9913ee3145ce0cfc1372ada8ada74bd287450313534b", "amount" : 20' http://localhost:3001/mineTransaction | json_pp
```

##### Get balance
```
curl http://localhost:3001/balance
```

#### Query information (UTXO) about a specific address 
```
curl http://localhost:3001/address/04f72a4541275aeb4344a8b049bfe2734b49fe25c08d56918f033507b96a61f9e3c330c4fcd46d0854a712dc878b9c280abe90c788c47497e06df78b25bf60ae64 | json_pp
```

##### Add peer
```
# connect the peer running on http port 3001
curl -H "Content-type:application/json" --data '{"peer" : "ws://localhost:6002"}' http://localhost:3001/addPeer

# connect the peer running on http port 3002
curl -H "Content-type:application/json" --data '{"peer" : "ws://localhost:6001"}' http://localhost:3002/addPeer
```
#### Query connected peers
```
curl http://localhost:3001/peers
```
