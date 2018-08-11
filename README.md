# Kempsie's Equihash Miner v0.0.1

kmpc supports the "classic" Equihash algorithm using the 200,9 parameters.

Equihash with 144,5 parameters will be released soon and is the projects highest priority.

All pools implemented with the stratum protocol are supported (e.g. flypool). Both SSL and non-SSL pools are supported.

Example usage for Zcash on encrypted flypool (Europe):

```sh
$ ./kmpc -s eu1-zcash.flypool.org -p 3443 -u your-public-wallet-address.worker-name --ssl --algorithm 200,9
```

Example usage for Zencash on un-encrypted suprnova with GPU 3 and 5:

```sh
$ ./kmpc -s zen.suprnova.cc -p 3618 -u your-account-name.worker-name --algorithm 200,9 --cuda-devices 3 5
```

## Roadmap in no particular order:

	144,5 support
		This is currently the highest prority for the project and is ongoing

	Windows support

	Remote stats monitoring for the user
		Already implemented - not production ready

	CPU usage optimisation

	User Interface

	Intensity options to keep target temperature per-GPU

	Multiple user pool support

	Configurable printing of kmpc's stats

	OpenCL implementation for AMD cards

	Please suggest more features here: https://github.com/kempsie/kmpc/issues

## Download Kempsie's kmpc miner:

https://github.com/kempsie/kmpc/releases

## Developer fee:

	0.5%

	Whilst features and performance are worked on, this low fee will remain.
	Once performance parity is achieved with other projects, the fee will be increased.

## Speed:

	kmpc displays current mining statistics per-GPU every 15 seconds.

	For more accurate stats - check the pool! The pool will estimate
	hashrate based on actual submitted shares from kmpc.

	0.5% of time spent mining is used towards the developer fee. For example,
	for every 60 seconds spent mining, 0.3 seconds is spent minig towards the developer
	fee. Unlike other miners, kmpc does not use a percentage of all valid shares
	as the dev fee (which would result in more shares for the developer).

## What coins can I mine?

	All equihash coins that use the 200,9 PoW algorithm: Zcash (ZEC), ZClassic (ZCL), Zencash (ZEN), etc

## Supported pools:

	All pools that support the stratum protocol are supported. For example:

	Supernova
	Flypool
	Miningpoolhub
	Nanopool

## SSL?

	Where possible, try and use pools that support SSL connections.
	This helps to protect your precious mining shares from being
	intercepted	by malicious third parties.

## User privacy, anonymity and security:

	This is extremley important to this project. kmpc does not monitor
	or collect ANY information whatsoever about its users.

	kmpc will open up two connections. One connetion is to the pool specified
	by the user (with the -s,--server and -p,--port options). The second connection
	is to the pool specified for the dev fee which uses an ssl connection.

	Please monitor traffic from kmpc to verify this statement. This project takes privacy
	very seriously.

	kmpc does not contain any malicious code or viruses that will intentionally harm your
	system.

## What operating systems does kmpc work on?

	Linux distros Ubuntu 14.04, 16.04 and 18.04 have been tested. kmpc should work with
	most if not all Linux distributions.

	Windows support is on the roadmap for kmpc.

## Supported GPUs:

	NVIDIA Maxwell and above

## Tested GPUs:

	GeForce GTX 1070
	GeForce GTX 1060 6GB
	GeForce GTX 970
	GeForce GTX 950

## kmpc output:
	User share submitted
		This means that a valid share has been mined by kmpc and has been submitted to your pool
	Dev share submitted
		This means that a valid share has been mined by kmpc and has been submitted to the dev pool
	User share accepted
		This means that a valid share that was previously submitted to your pool has been accepted by your pool
	Dev share accepted
		This means that a valid share that was previously submitted to the dev pool has been accepted by the dev pool

## Command-Line arguments:

	Kempsie's Equihash Miner
	Usage: kmpc [OPTIONS]

	Information:
		-h,--help                   Print this help message and exit
		--list-algorithms           Lists each Equihash variant with a non-exhaustive list of coins that use the variant and exits
		--list-cuda-devices         Lists each CUDA device by ID and exits
		-v,--version                Prints the version of kmpc and exits

	Options:
		--algorithm TEXT Needs: --server --port --user
									Which Equihash algorithm to use. For example, "200,9". Find list of algorithms with --list-algorithms
		-b,--benchmark              Run a quick benchmark of the Equihash algorithm, report the results and exit
		--cuda-devices INT ...      Space seperated list of CUDA GPU IDs. Default is to use all GPUs. Find list of GPUs with --list-cuda-devices

	Stratum Server - Pool:
		-s,--server TEXT Needs: --algorithm --port --user
									Stratum server. E.g. zen.suprnova.cc
		-p,--port INT Needs: --algorithm --server --user
									Stratum server port number. E.g. 3618
		-u,--user TEXT Needs: --algorithm --server --port
									Stratum server user. This is usually your public wallet address
		--password TEXT Needs: --algorithm --server --port --user
									Stratum server password. Often unused. Use 'X' if unsure
		--ssl Needs: --algorithm --server --port --user
									For pools encrypted with SSL, set this flag
