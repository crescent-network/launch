# Gentx Cli Command
```bash
# Use git to clone the source code and install `crescentd`
git clone https://github.com/crescent-network/launch
cd launch/mainnet/
crescentd init <validator-name>
rm ~/.crescent/config/genesis.json
tar -zxvf crescent-1-genesis-for-gentx.json.tar.gz
cp crescent-1-genesis-for-gentx.json ~/.crescent/config/genesis.json
crescentd gentx <validator-keyname> 1000000ucre --commission-max-change-rate 1 --commission-max-rate 1  --commission-rate 0.2 --min-self-delegation 1 --pubkey=$(crescentd tendermint show-validator) --chain-id crescent-1
cd ~/.crescent/config/gentx
```
Please PR the json file in gentx folder.

## Genesis hash check
```
jq -S -c -M '' ~/.crescent/config/genesis.json | shasum -a 256
468e6c92ff952f106bb1898d90f5e5ab1e8e03cd615beb80e1d4cd5029e45a47
```
