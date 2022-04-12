# Chain start Cli Command
Mainnet genesis binary version\
https://github.com/crescent-network/crescent/releases/tag/v1.0.0

```bash
# Use git to clone the source code and install `crescentd`
git clone https://github.com/crescent-network/launch
cd launch/mainnet/
tar -zxvf genesis.json.tar.gz
cp genesis.json ~/.crescent/config/genesis.json
crescentd start
```
## Genesis hash check
```
jq -S -c -M '' ~/.crescent/config/genesis.json | shasum -a 256 
7e1dcc12fc0dccb4230768bf91311980313d5a6f67da5e4b97d29304b293ce2b
```

# Node Config

## Spec
```
CPU: 8core
RAM: 32gb
DISK: r/w - 100mb/300mb , iops r/w - 1k/1k
      (Capacity needs to be set fluidly depending on network conditions)
recommended region: Tokyo
recommended Providers: aws , gcp
```
The minimum specification is 4c/16gb.

However, the upgrade is likely to take place within six months. This is optional.

## Node Config
app.toml
```
minimum-gas-prices = "0ucre"
```

## P2P info
seeds
```
929f22a7b04ff438da9edcfebd8089908239de44@18.180.232.184:26656
```

persistent_peers(Will continue to be added)
```
68787e8412ab97d99af7595c46514b9ab4b3df45@54.250.202.17:26656
```