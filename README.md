# Sentinel CLI Client

[![Tag](https://img.shields.io/github/tag/sentinel-official/cli-client.svg)](https://github.com/sentinel-official/cli-client/releases/latest)
[![GoReportCard](https://goreportcard.com/badge/github.com/sentinel-official/cli-client)](https://goreportcard.com/report/github.com/sentinel-official/cli-client)
[![Licence](https://img.shields.io/github/license/sentinel-official/cli-client.svg)](https://github.com/sentinel-official/cli-client/blob/development/LICENSE)
[![LoC](https://tokei.rs/b1/github/sentinel-official/cli-client)](https://github.com/sentinel-official/cli-client)

Download the latest version of CLI client software from the releases section [here](https://github.com/sentinel-official/dvpn-node/releases/latest "here").

## Install WireGuard

### Linux

```sh
sudo apt-get update && \
sudo apt install wireguard-tools
```

### Mac

```sh
TBU
```

## Connect to a dVPN node

1. Create or recover a key

    ```sh
    sentinelcli keys add \
        --home "${HOME}/.sentinelcli" \
        --keyring-backend file \
        <KEY_NAME>
    ```

    Pass flag `--recover` to recover the key

2. Query the active nodes and choose one

    ```sh
    sentinelcli query nodes \
        --home "${HOME}/.sentinelcli" \
        --node https://rpc.sentinel.co:443 \
        --status Active \
        --page 1
    ```

    Increase the page number to get more nodes

3. Subscribe to a node

    ```sh
    sudo sentinelcli subscription subscribe-to-node \
        --home "${HOME}/.sentinelcli" \
        --keyring-backend file \
        --chain-id sentinelhub-2 \
        --node https://rpc.sentinel.co:443 \
        --from <KEY_NAME> \
        <NODE_ADDRESS> <DEPOSIT>
    ```

4. Connect

    ```sh
    sudo sentinelcli connect \
        --home "${HOME}/.sentinelcli" \
        --keyring-backend file \
        --chain-id sentinelhub-2 \
        --node https://rpc.sentinel.co:443 \
        --yes \
        --from <KEY_NAME> \
        <SUBSCRIPTION_ID> <NODE_ADDRESS>
    ```

## Disconnect from a dVPN node

1. Disconnect

    ```sh
    sudo sentinelcli disconnect \
        --home "${HOME}/.sentinelcli"
    ```

Click [here](https://github.com/sentinel-official/docs/tree/master/guides/clients/cli "here") to know more!
