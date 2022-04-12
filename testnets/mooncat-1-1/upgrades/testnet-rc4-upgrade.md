# mooncat-1-1, testnet-rc4 Upgrade, Instructions

This document describes the steps for validator and full node operators for the successful execution of the `testnet-rc4`

Proposal 26 : [mintscan](https://testnet.mintscan.io/crescent/proposals/26), [nodes.guru](https://testnet.explorer.crescent.nodes.guru/proposal/26)

Chain ID : mooncat-1-1

Upgrade Name : ****testnet-rc4****

Upgrade Height : 365000

Expected Upgrade Time : about UTC 2022-04-12 00:23:40

Binary : Crescent [v1.0.0-rc3](https://github.com/crescent-network/crescent/releases/tag/v1.0.0-rc3) -> [v1.0.0-rc4](https://github.com/crescent-network/crescent/releases/tag/v1.0.0-rc4)

## Upgrade will take place April 12, 2022

The upgrade will take place at a block height of `365000`. At the time of writing, and at current block times (around 5.7s/block), this block height corresponds approximately to `UTC 2022-04-12 00:23:40`. This date/time is approximate as blocks are not generated at a constant interval. 

## Chain-id will remain the same

The chain-id of the network will remain the same, `mooncat-1-1`. This is because an in-place migration of state will take place, i.e., this upgrade does not export any state.

## Preparing for the upgrade

### **Backups**

Prior to the upgrade, validators are encouraged to take a full data snapshot. Snapshotting depends heavily on infrastructure, but generally this can be done by backing up the `.crescent` directory. If you use Cosmovisor to upgrade, by default, Cosmovisor will backup your data upon upgrade.

It is critically important for validator operators to back-up the `.crescent/data/priv_validator_state.json` file after stopping the crescentd process. This file is updated every block as your validator participates in consensus rounds. It is a critical file needed to prevent double-signing, in case the upgrade fails and the previous chain needs to be restarted.

### Current runtime, mooncat-1-1 is running Crescent v1.0.0-rc3

The Crescent testnet network, `mooncat-1-1`, is currently running [Crescent v1.0.0-rc3](https://github.com/crescent-network/crescent/releases/tag/v1.0.0-rc3).

### Target runtime, mooncat-1-1 (post testnet-rc4 upgrade) will run Crescent v1.0.0-rc4

The Crescent testnet network, `mooncat-1-1`, will run [Crescent v1.0.0-rc4](https://github.com/crescent-network/crescent/releases/tag/v1.0.0-rc4) Operators *MUST* use this version post-upgrade to remain connected to the network.

## testnet-rc4 upgrade steps

There are 2 major ways to upgrade a node:

- Manual upgrade
- Upgrade using [Cosmovisor](https://github.com/cosmos/cosmos-sdk/tree/master/cosmovisor)
    - by manually preparing the new binary

If you prefer to use Cosmovisor to upgrade, some preparation work is needed before upgrade.

### Method I: manual upgrade (Recommended)

Run Crescent v1.0.0-rc3 till upgrade height, the node will panic:

```
ERR UPGRADE "testnet-rc4" NEEDED at height: 365000

ERR CONSENSUS FAILURE!!! err="UPGRADE "testnet-rc4" NEEDED at height: 365000

```

Stop the node, and install [Crescent v1.0.0-rc4](https://github.com/crescent-network/crescent/releases/tag/v1.0.0-rc4) and re-start by `crescentd start`.

It may take 20 min to a few hours until validators with a total sum voting power > 2/3 to complete their nodes upgrades. After that, the chain can continue to produce blocks.

### Method II: upgrade using Cosmovisor by manually preparing the Crescent v1.0.0-rc4 binary

### Preparation

Install the latest version of Cosmovisor:

```bash
go install github.com/cosmos/cosmos-sdk/cosmovisor/cmd/cosmovisor@v1.0.0

```

Create a cosmovisor folder:

create a Cosmovisor folder inside `$CRESCENT_HOME` and move Crescent v1.0.0-rc3 into  `$CRESCENT_HOME/cosmovisor/genesis/bin`

```bash
export CRESCENT_HOME={SET_YOUR_CRESCENT_HOME}
$(which crescentd) version
# should be 1.0.0-rc3

mkdir -p $CRESCENT_HOME/cosmovisor/genesis/bin
cp $(which crescentd) $CRESCENT_HOME/cosmovisor/genesis/bin
```

build Crescent v1.0.0-rc4, and move crescentd v1.0.0-rc4 to `$CRESCENT_HOME/cosmovisor/upgrades/testnet-rc4/bin`

```bash
export CRESCENT_RC3_PATH={SET_YOUR_PATH}
$CRESCENT_RC3_PATH version
# should be 1.0.0-rc4

mkdir -p  $CRESCENT_HOME/cosmovisor/upgrades/testnet-rc4/bin
cp $CRESCENT_RC3_PATH $CRESCENT_HOME/cosmovisor/upgrades/testnet-rc4/bin

```

Then you should get the following structure:

```
.
├── current -> genesis or upgrades/<name>
├── genesis
│   └── bin
│       └── crescentd  #v1.0.0-rc3
└── upgrades
└── testnet-rc4
└── bin
    └── crescentd  #v1.0.0-rc4

```

Export the environmental variables:

```bash
export DAEMON_NAME=crescentd
# please change to your own crescent home dir
export DAEMON_HOME=$CRESCENT_HOME
export DAEMON_RESTART_AFTER_UPGRADE=true

```

Start the node:

```bash
cosmovisor start --x-crisis-skip-assert-invariants

```

### Expected ugprade result

When the upgrade block height is reached, you can find the following information in the log:

```
ERR UPGRADE "testnet-rc4" NEEDED at height: 365000: upgrade to testnet-rc4 and applying upgrade "testnet-rc4" at height:365000.

```

This may take 20 min to a few hours.
After this, the chain will continue to produce blocks when validators with a total sum voting power > 2/3 complete their nodes upgrades.

### ~~Method III: upgrade using Cosmovisor by auto-downloading the Crescent ****v1.0.0-rc4**** binary~~

This update is not applicable for this method, `binaries` is not set to upgrade-info of upgrade proposal, so please use method 1 and 2.

## Upgrade duration

The upgrade may take several hours to complete because `mooncat-1-1` participants operate globally with differing operating hours and it may take some time for operators to upgrade their binaries and connect to the network.

## Rollback plan

During the network upgrade, core Crescent teams will be keeping an ever vigilant eye and communicating with operators on the status of their upgrades. During this time, the core teams will listen to operator needs to determine if the upgrade is experiencing unintended challenges. In the event of unexpected challenges, the core teams, after conferring with operators and attaining social consensus, may choose to declare that the upgrade will be skipped.

Steps to skip this upgrade proposal are simply to resume the mooncat-1-1 network with the (downgraded) v1.0.0-rc3 binary using the following command:

> crescentd start --unsafe-skip-upgrade 365000
>

Note: There is no particular need to restore a state snapshot prior to the upgrade height, unless specifically directed by core Crescent teams.

Important: A social consensus decision to skip the upgrade will be based solely on technical merits, thereby respecting and maintaining the decentralized governance process of the upgrade proposal's successful YES vote.

## Communications

Operators are encouraged to join the `#validators-general` channel of the Crescent Network Community Discord. This channel is the primary communication tool for operators to ask questions, report upgrade status, report technical issues, and to build social consensus should the need arise. 

## Risks

As a validator performing the upgrade procedure on your consensus nodes carries a heightened risk of double-signing and being slashed. The most important piece of this procedure is verifying your software version and genesis file hash before starting your validator and signing.

The riskiest thing a validator can do is discover that they made a mistake and repeat the upgrade procedure again during the network startup. If you discover a mistake in the process, the best thing to do is wait for the network to start before correcting it.

## Reference

[Cosmos Hub 4, Vega Upgrade, Instructions](https://github.com/cosmos/gaia/blob/main/docs/migration/cosmoshub-4-vega-upgrade.md)
