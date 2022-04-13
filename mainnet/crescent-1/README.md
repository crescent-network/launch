# Chain start Cli Command
Mainnet genesis binary version

https://github.com/crescent-network/crescent/releases/tag/v1.0.0

```bash
# Use git to clone the source code and install `crescentd`
git clone https://github.com/crescent-network/launch
cd launch/mainnet/crescent-1
tar -zxvf genesis.json.tar.gz
mkdir -p ~/.crescent/config
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
68787e8412ab97d99af7595c46514b9ab4b3df45@54.250.202.17:26656,0ed5ed53ec3542202d02d0d47ac04a2823188fc2@52.194.172.170:26656,04016e800a079c8ee5bdb9361c81c026b6177856@34.146.27.138:26656,24be64cd648958d9f685f95516cb3b248537c386@52.197.140.210:26656,83b3ba06b43fda52c048934498c6ee2bd4987d2d@3.39.144.72:26656,7e59c83196fdc61dcf9d36c42776c0616bc0fc8c@3.115.85.120:26656,06415494b86316c55245d162da065c3c0fee83fc@172.104.108.21:26656,4293ce6b47ee2603236437ab44dc499519c71e62@45.76.97.48:26656,4113f7496857d3f161921c7af8d62022551a7e6b@167.179.75.240:26656,2271e3739ea477bce0df39dd9e95f8b952a2106e@198.13.62.7:26656,b34115ba926eb12059ca0ade4d1013cac2f8d289@crescent-mainnet-01.01node.com:26656,d7556e41ba2f333379f6d87b1af3cce2ca545f79@34.88.102.246:26656,26011ac36240fb49852cc7196f71a1884434b8c4@34.84.227.139:26656,b840926fb6a2bd04fc70e501002f9286655c9179@52.199.91.143:30732,86030850dd635cab1f136979568087407a025491@46.101.153.158:26656,3bcffbcb11e96edc84c04a5628639f5ed94b9db2@128.0.51.5:26656,3b468af82b8ffa049b3e1f67dc4615a31ec8f01e@50.21.167.131:26656
```
