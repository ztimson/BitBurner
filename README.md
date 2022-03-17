# BitBurner - Scripts
These scripts are for playing the [open source](https://github.com/danielyxie/bitburner) game [BitBurner](https://danielyxie.github.io/bitburner/)

## Table of Contents
- [BitBurner - Scripts](#bitburner-scripts)
  - [Table of Contents](#table-of-contents)
  - [Quick Start](#quick-start)
  - [Scripts](#scripts)
    - [connect.js](#connectjs)
    - [copy.js](#copyjs)
    - [crawler.js](#crawlerjs)
    - [hacknet-manager.js](#hacknet-managerjs)
    - [miner.js](#minerjs)
    - [network-graph.js](#network-graphjs)
    - [rootkit.js](#rootkitjs)
    - [update.js](#updatejs)

## Quick Start

```bash
# Download the update script in-game
wget https://gitlab.zakscode.com/ztimson/BitBurner/-/raw/develop/scripts/update.js scripts/update.js

# Run the update script (Repeat this to pull this repository in the future)
run scripts/update.js

# Start the node manager with 8 nodes
run scripts/node-manager.js 8

# Chain the crawler, rootkit & miner to hack everything on the network
alias hackAll="run scripts/crawler.js /scripts/rootkit.js {{TARGET}} /scripts/miner.js"
hackAll

# Identify & install a backdoor on CSEC
run scripts/network-graph.js -f CSEC
run scripts/rootkit.js CSEC
run scripts/connect.js CSEC
backdoor
```

Learn more about the [availible scripts](#scripts) bellow or pass the `--help` flag to any of the included scripts in-game.

## Scripts

### [connect.js](./scripts/connect.js)
**RAM:** 1.85 GB

Search the network for a device and connect to it.
```
[home ~/]> run /scripts/connect.js --help
Running script with 1 thread(s), pid 1 and args: ["--help"].
/scripts/connect.js: 

Search the network for a device and connect to it.

Usage:	run connect.js DEVICE
	run connect.js --help

	DEVICE			 Device to connect to

Options:
	-h --help		 Display this help message
```

### [copy.js](./scripts/copy.js)
**RAM:** 3.50 GB

Copy a file/script to a device along with any dependencies.
```
[home ~/]> run scripts/copy.js --help
Running script with 1 thread(s), pid 1 and args: ["--help"].
/scripts/copy.js: 

Copy a file/script to a device along with any dependencies.

Usage:	run copy.js [OPTIONS] FILE DEVICE
	run copy.js --help

	FILE			 File to copy
	DEVICE			 Device to copy file(s) to

Options:
	-d --no-deps		 Skip copying dependencies
	-s --silent		 Surpress program output
	-h --help		 Display this help message
```

### [crawler.js](./scripts/crawler.js)
**RAM:** 4.10 GB

Search the network for devices to execute a script against.
```
[home ~/]> run scripts/crawler.js --help
Running script with 1 thread(s), pid 1 and args: ["--help"].
/scripts/crawler.js: 

Search the network for devices to execute a script against.

Usage:	run crawler.js [OPTIONS] SCRIPT [ARGS]...
	run crawler.js --help

	SCRIPT			 Script to copy & execute
	ARGS			 Arguments for script. Forward the current target with: {{TARGET}}

Options:
	-c --cpu		 Number of CPU threads to use with script
	-d --depth		 Depth to scan to, defaults to 3
	-l --level		 Exclude targets with higher hack level, defaults to current hack level
	-p --ports		 Exclute targets with too many closed ports
	-s --silent		 Surpress program output
	-h --help		 Display this help message
```

### [hacknet-manager.js](./scripts/hacknet-manager.js)
**RAM:** 5.70 GB

Buy, upgrade & manage Hacknet nodes automatically. Tail for live updates.
```
[home ~/]> run scripts/hacknet-manager.js --help
Running script with 1 thread(s), pid 1 and args: ["--help"].
/scripts/hacknet-manager.js: 

Buy, upgrade & manage Hacknet nodes automatically. Tail for live updates.

Usage:	run hacknet-manager.js [OPTIONS] [LIMIT]
	run hacknet-manager.js --help

	LIMIT			 Limit the number of nodes the manager will buy, defaults to 8

Options:
	-b --balance		 Prevent spending bellow point
	-s --sleep		 Amount of time to wait between purchases, defaults to 1 (second)
	-h --help		 Display this help message
```

### [miner.js](./scripts/miner.js)
**RAM:** 2.45 GB

Weaken, Grow, Hack loop to "mine" device for money. Tail for live updates.
```
[home ~/]> run scripts/miner.js --help
Running script with 1 thread(s), pid 1 and args: ["--help"].
/scripts/miner.js: 

Weaken, Grow, Hack loop to "mine" device for money. Tail for live updates.

Usage:	run miner.js [DEVICE]
	run miner.js --help

	DEVICE			 Device to mine, defaults to current machine

Options:
	-h --help		 Display this help message
```

### [network-graph.js](./scripts/network-graph.js)
**RAM:** 3.85 GB

Scan the network for devices and display as an ASCII tree.
```
[home ~/]> run /scripts/network-graph.js --help
Running script with 1 thread(s), pid 1 and args: ["--help"].
/scripts/network-graph.js: 

Scan the network for devices and display as an ASCII tree:
 home
  ├─ n00dles (ROOTED)
  |   └─ max-hardware (80|1)
  |       └─ neo-net (50|1)
  ├─ foodnstuff (ROOTED)
  └─ sigma-cosmetics (ROOTED)

Usage:	run network-graph.js [OPTIONS] [DEVICE]
	run network-graph.js --help

	DEVICE			 Point to start scan from, defaults to current machine

Options:
	-d --depth		 Depth to scan to, defaults is 3
	-f --filter		 Filter to device matching name
	-e --regex		 Filter to devices matching pattern
	-r --rooted		 Filter to devices that have been rooted
	-n --not-rooted		 Filter to devices that have not been rooted
	-v --verbose		 Display the required hack level & number of ports to root: (level|port)
	-h --help		 Display this help message
```

### [rootkit.js](./scripts/rootkit.js)
**RAM:** 4.75 GB - 4.90 GB <small>(depending on un-commented programs)</small>

Automatically gain root on a target machine. A file can also be uploaded & executed.

Programs can be commented out to lower the cost of running.
```
[home ~/]> run scripts/rootkit.js --help
Running script with 1 thread(s), pid 1 and args: ["--help"].
/scripts/rootkit.js: 

Automatically gain root access to a device. A file can also be uploaded & executed.

Usage:	run rootkit.js [OPTIONS] [DEVICE] [SCRIPT] [ARGS]...
	run rootkit.js --help

	DEVICE			 Device to root, defaults to current machine
	SCRIPT			 Script to copy & execute
	ARGS			 Arguments for script. Forward the current target with: {{TARGET}}

Options:
	-c --cpu		 Number of CPU threads to use with script
	-s --silent		 Surpress program output
	-h --help		 Display this help message
```

### [update.js](./scripts/update.js)
**RAM:** 2.65 GB

Download the latest script updates from the repository using wget.
```
[home ~/]> run scripts/update.js --help
Running script with 1 thread(s), pid 1 and args: ["--help"].
/scripts/update.js: 

Download the latest script updates from the repository using wget.

Usage:	run update.js [OPTIONS] [DEVICE]
	run update.js --help

	DEVICE			 Device to update, defaults to current machine

Options:
	--skip-self		 Skip updating self (for debugging & used internally)
	--no-banner		 Hide the banner (Used internally)
	-h --help		 Display this help message
```
