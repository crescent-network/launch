# Genesis

```
wget https://blocksnapshot.s3.ap-northeast-2.amazonaws.com/mooncat-2-genesis.json

jq -S -c -M '' mooncat-2-genesis.json | shasum -a 256
539416248f0f4501a5effed4b51b4908b4f3a3f025944a48e0476237a035828a
```

# Testnet Information

## Crescent Binary

Start is attempted with V2. Follow the upgrade procedure
```bash
# Use git to clone the source code and install `crescentd`
git clone https://github.com/crescent-network/crescent
cd crescent
git checkout v2.1.1
make install-testing
```

## Node
```
717b2c0e3a4a7d6785b8072802b1c39262226685@34.147.9.210:16656,5065dab6eb16305b611dcaca57dd93f2bc1f0bb0@35.221.85.152:26656
```
