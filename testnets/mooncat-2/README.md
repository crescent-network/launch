# Genesis

```
wget https://blocksnapshot.s3.ap-northeast-2.amazonaws.com/mooncat-2-genesis.json

jq -S -c -M '' mooncat-2-genesis.json | shasum -a 256
67579e3d15d0568fe9b9379a3d4076fbb57e9e813d5bed14352086c8688fcdeb
```

# Testnet Information

## Crescent Binary

Start is attempted with V2. Follow the upgrade procedure
```bash
# START HEIGHT = 3126050
# Use git to clone the source code and install `crescentd`
git clone https://github.com/crescent-network/crescent
cd crescent
git checkout v2.3.0
make install-testing
crescentd start --halt-height 3126350
# halt node
git checkout v3.0.0-rc5
make install-testing
crescentd start 
```

## Node
```
717b2c0e3a4a7d6785b8072802b1c39262226685@34.147.9.210:16656,5065dab6eb16305b611dcaca57dd93f2bc1f0bb0@35.221.85.152:26656
```
