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
