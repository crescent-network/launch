# Genesis

```
wget https://blocksnapshot.s3.ap-northeast-2.amazonaws.com/mooncat-2-external.json

jq -S -c -M '' mooncat-2-external.json | shasum -a 256
8bdf827a6626067b778767890a4fcdedf2afd73c2ba2a1f8663de93235078023
```

# Testnet Information

## Crescent Binary

Start is attempted with V2. Follow the upgrade procedure
```bash
# START HEIGHT = 3815000
# Use git to clone the source code and install `crescentd`
git clone https://github.com/crescent-network/crescent
cd crescent
git checkout v2.3.0
make install
crescentd start --halt-height 3815100
# halt node
git checkout v3.0.0
make install
crescentd start 
```
## Quick Start(state sync)
Pass the synchronization of the previous block, and quickly reach the latest block

However, it is not possible to check the omitted block data. Additionally, you do not need to upgrade to start with the latest block

```bash
git clone https://github.com/crescent-network/crescent
cd crescent
git checkout v3.0.0
make install

#!/bin/bash

SNAP_RPC="http://52.74.77.1:26657"

LATEST_HEIGHT=$(curl -s $SNAP_RPC/block | jq -r .result.block.header.height); \
BLOCK_HEIGHT=$((LATEST_HEIGHT - 500)); \
TRUST_HASH=$(curl -s "$SNAP_RPC/block?height=$BLOCK_HEIGHT" | jq -r .result.block_id.hash)

sed -i.bak -E "s|^(enable[[:space:]]+=[[:space:]]+).*$|\1true| ; \
s|^(rpc_servers[[:space:]]+=[[:space:]]+).*$|\1\"$SNAP_RPC,$SNAP_RPC\"| ; \
s|^(trust_height[[:space:]]+=[[:space:]]+).*$|\1$BLOCK_HEIGHT| ; \
s|^(trust_hash[[:space:]]+=[[:space:]]+).*$|\1\"$TRUST_HASH\"|" $HOME/.crescent/config/config.toml

#Download the data chunk for approximately 10 minutes.
crescentd start

```

## Node-peer
```
89760782cc1fcf11ca8a1cdc3494a8d788699313@52.74.77.1:26656
```
## endpoint
```
https://testnet-endpoint.crescent.network:26657/
https://testnet-endpoint.crescent.network:1317/
testnet-endpoint.crescent.network:9090
```