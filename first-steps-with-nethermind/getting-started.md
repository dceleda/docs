---
description: A quick start example for Görli Testnet Nethermind synchronization
---

# Getting Started

## 🔧 Setting up a Virtual Machine

If you are not launching on your laptop/desktop, then you will probably want to setup a cloud VM. You can find more info about setting up everything with selected [cloud providers](../guides-and-helpers/cloud-providers/).

{% page-ref page="../guides-and-helpers/cloud-providers/" %}

Make sure that you configure [firewall](firewall-configuration.md) properly.

{% page-ref page="firewall-configuration.md" %}

You can check [supported operating systems](supported-platforms.md) and architectures and [hardware requirements](hardware-requirements.md).

{% page-ref page="supported-platforms.md" %}

{% page-ref page="hardware-requirements.md" %}

## ⏬ Downloading Nethermind

You need to download the Nethermind package first. There are currently 2 sources providing `Nethermind` packages. Check this page to find them out

{% page-ref page="../ethereum-client/download-sources/" %}

## 🔛 Launching Nethermind

* After launching Nethermind via `./Nethermind.Launcher` you need to choose the Node to start first.

![Nethermind.Launcher initial options](../.gitbook/assets/getting_started_0.png)

* First select `Ethereum Node` and then select `Goerli (light Clique testnet)`

![Network options](../.gitbook/assets/getting_started_1.png)

* Select `Fast Sync` mode. If you are curious about other modes, click here: [sync modes](https://docs.nethermind.io/nethermind/ethereum-client/sync-modes).

![Selecting Fast sync option](../.gitbook/assets/getting_started_2.png)

* Ensure that JSON RPC is enabled by typing `y`and pressing `enter`
* Press `enter` to skip setting up `Host IP` 127.0.0.1 will be set as default

{% hint style="warning" %}
If **not** running local, you may need to change the `Host` value to the VM public IP address.
{% endhint %}

![Enabling JSON RPC via Nethermind.Launcher](../.gitbook/assets/getting_started_3.png)

* Skip the `ethstats registration` by typing `N` and pressing `enter`.

![EthStats configuration skip](../.gitbook/assets/getting_started_4.png)

## 👨💻 Explaining Nethermind logs

After the node starts, you will see some initial info about the node and then the sync will start. Görli fast sync uses a `fast blocks` sync mode initially. The `fast blocks` sync picks some known `pivot block` from the past and downloads `headers`, `bodies`, and `receipts` downwards all the way to `genesis block`. All blocks from 0 to the `pivot block` are showed as `Old Headers` in the `fast blocks sync` logs. The console display shows the number growing from 0 to pivot, but this is just to make the display more user-friendly.

You will see some information about the sync progress, like below:

1. Shows the number of already downloaded `headers`, `bodies` and `receipts` under the name `Downloaded` out of all to be downloaded in the fast blocks stage.
2. Shows the current queue of already downloaded `blocks`, `headers` and `receipts` waiting for being saved to the database.
3. Shows the current download speed \(blocks per second - bps\).
4. Shows the average download speed \(blocks per second - bps\).

![Fast blocks sync logs](../.gitbook/assets/getting_started_log_0.png)

When the fast blocks stage finishes, there will be some period of downloading blocks between the `pivot` and the`latest blocks` which will have some additional info:

1. Shows the last entry from the fast blocks stage.
2. Shows the mode transition moment.
3. Displays the speed \(in blocks per second\) of all `headers`, `bodies` and `receipts` at the same time.
4. Additional info will appear every 30000 blocks with information about the Görli epoch being stored.

![G&#xF6;rli fast sync logs](../.gitbook/assets/getting_started_7.png)

After the `fast sync` part finished, the node will transition to the `state sync stage` when the `state trie` is being downloaded. Much information is displayed about the progress, as this process may take a long time on mainnet \(a few hours\).

1. Total elapsed time in `state sync` is displayed.
2. The total percentage of downloaded DB size is displayed \(on mainnet the sync finishes around 34GB in March 2020, on Görli around 800MB\).
3. `branches` stands for the percentage of downloaded branches.
4. Download speed in kilobytes per second is displayed.
5. `accounts` stands for the number of accounts data downloaded already.
6. `nodes` stands for the number of `Patricia trie nodes` downloaded by the sync process.
7. `diagnostic` shows the time spent in the DB write / read access. The higher the value, the worse. It may get much worse if you restart the node during the sync process, as we need to recreate some caches then by reading data from the DB.

![G&#xF6;rli state sync logs](../.gitbook/assets/getting_started_8.png)

When the state sync is nearing completion, you may see a series of `branch sync` information reloading many times from 0% to nearly 100%. This is the node trying to retrieve the few remaining state nodes and progressing with the head block rapidly:

![G&#xF6;rli branch sync logs](../.gitbook/assets/getting_started_26.png)

At some point, the entire state is downloaded and the node enters the `full sync` mode and will allow you to issue CLI / Web3 queries and send / receive transactions🥳

1. The `root` is saved at the moment when the entire `Patricia trie` is downloaded.
2. We also clearly state that the node transitions to the `full sync`.
3. When you see the block being processed, then you are in the `full sync` and the newly arrived block is being calculated.
4. Every two minutes you will see a summary of connected peers with their client version, IP address, highest synced block, and data download speeds.

![G&#xF6;rli full sync logs](../.gitbook/assets/getting_started_9.png)

Now you can launch CLI in the separate process \(launching `Nethermind.Launcher` again and selecting CLI instead of Node\). You can read more about [CLI here](https://docs.nethermind.io/nethermind/nethermind-utilities/cli).

You can also connect to the node from [Metamask](https://metamask.io/) by selecting `localhost:8545` from the Metamask network list.

![Metamask localhost connection](https://github.com/NethermindEth/nethermind/raw/master/docs/source/metamask/localhost.png)



