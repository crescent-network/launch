# mooncat-1-1, testnet-v1.1.0 Upgrade, Instructions

This document describes the steps for validator and full node operators for the successful execution of the `testnet-v1.1.0`

Chain ID : mooncat-1-1

Upgrade Name : ****testnet-v1.1.0****

Upgrade Height : 1072528

Binary : Crescent [v1.0.0-rc4](https://github.com/crescent-network/crescent/releases/tag/v1.0.0-rc4) -> [v1.1.0](https://github.com/crescent-network/crescent/releases/tag/v1.1.0)

## Upgrade on 1072528 height, without upgrade proposal

The upgrade occurred in block 1072528 without the upgrade proposal, so you have to change the binary from  [v1.0.0-rc4](https://github.com/crescent-network/crescent/releases/tag/v1.0.0-rc4) to [v1.1.0](https://github.com/crescent-network/crescent/releases/tag/v1.1.0) after setting `crescentd start --halt-height 1072528` with v1.0.0-rc4

## Chain-id will remain the same

The chain-id of the network will remain the same, `mooncat-1-1`. This is because an in-place migration of state will take place, i.e., this upgrade does not export any state.

## Preparing for the upgrade

### **Backups**

It is critically important for validator operators to back-up the `.crescent/data/priv_validator_state.json` file after stopping the crescentd process. This file is updated every block as your validator participates in consensus rounds. It is a critical file needed to prevent double-signing, in case the upgrade fails and the previous chain needs to be restarted.

## Communications

Operators are encouraged to join the `#validators-general` channel of the Crescent Network Community Discord. This channel is the primary communication tool for operators to ask questions, report upgrade status, report technical issues, and to build social consensus should the need arise. 

## Risks

As a validator performing the upgrade procedure on your consensus nodes carries a heightened risk of double-signing and being slashed. The most important piece of this procedure is verifying your software version and genesis file hash before starting your validator and signing.

The riskiest thing a validator can do is discover that they made a mistake and repeat the upgrade procedure again during the network startup. If you discover a mistake in the process, the best thing to do is wait for the network to start before correcting it.

## Reference

[mooncat-1-1, testnet-rc4 Upgrade, Instructions](https://github.com/crescent-network/launch/blob/main/testnets/mooncat-1-1/upgrades/testnet-rc4-upgrade.md)
