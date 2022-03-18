# Gentx Cli Command
```bash
# Use git to clone the source code and install `crescentd`
git clone https://github.com/crescent-network/launch
cd launch/testnet/
crescentd init <validator-name>
rm ~/.crescent/config/genesis.json
tar -zxvf genesis.json.tar.gz
cp genesis.json ~/.crescent/config/
crescentd gentx <validator-keyname> 1000000ucre --commission-max-change-rate 1 --commission-max-rate 1  --commission-rate 0.2 --min-self-delegation 1 --pubkey=$(crescentd tendermint show-validator) --chain-id mooncat-1-1
cd ~/.crescent/config/gentx
```
Please PR the json file in gentx folder.

## Genesis hash check
```
jq -S -c -M '' ~/.crescent/config/genesis.json | shasum -a 256
b2e097a4415757281a1611090c54e0187d0c9933991a07eed8423beea5a8ce1b
```


# Tentnet info
```bash
# Use git to clone the source code and install `crescentd`
git clone https://github.com/crescent-network/launch
cd launch/testnet/
rm ~/.crescent/config/genesis.json
tar -zxvf genesis_collect-gentxs.json.tar.gz
cp genesis_collect-gentxs.json ~/.crescent/config/genesis.json
crescentd start
```
## Seed
```
1fe40daaf2643fd3857e30f86ff30ea82bf1c03b@54.169.204.99:26656
```

## Node
```
2d8e31ad11b840c5ce7f1900b4da3a3bcf0985ef@139.59.151.125:26656,09e76cfbe89357d6bb3b16c4d013f420721b6664@50.18.111.23:26656,3802abfdf8a1c0a60041e684b08b6bec92d0a325@178.62.19.161:26656,2821cee54928a0fe1db97376ae7c48c4f0a9528a@137.184.127.205:26656,b2d2685e01641264fff25f5b3be23eacbdf9b08d@3.35.211.36:26656,29b006edeb2e0ee9bbe05060ebc6550549dc656e@218.53.140.56:20406,e2f735b5ecb6f909d09f4e3ebce6a90c63d18fbe@59.13.223.197:30535,b91b8ab43d8fc161587f09a09ccbb7fda7c41beb@37.120.245.39:26656,841f1cfa0174017813e2291cfa845001391a2cee@crescent-testnet.01no.de:26656
```
## Collected Genesis hash check
```
jq -S -c -M '' ~/.crescent/config/genesis.json | shasum -a 256
9fbbb4a80d6effdfc0845bfbf19ba1e323b758a934797e2b17621f149aadb0da
```
