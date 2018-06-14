# Mining

## Pool mining
**LitecoinEco** can be mined only by CPU thanks to YescryptECO hashing algorithm. GPU mining can be done too, but it is very slow and unefficient, that's why there is no GPU mining software available. This article is about how to mine LitecoinEco on CPU only.

### Mine LitecoinEco on Windows:

#### Mine with LitecoinEco GUI Miner:
- Download and install / unpack the latest version of [**LitecoinEco GUI Miner**](https://github.com/litecoineco/litecoineco-gui-miner/releases) for Windows from GitHub
- Run **Eliminer.exe**
- Set your wallet address and click on **Start mining** button

*Note that LitecoinEco GUI Miner is just a GUI for cpuminer-opt, it doesn't represent any additional advantage than user friendly interface.*

#### Mine with cpuminer-opt:
- Download the latest version of [**cpuminer-opt**](https://github.com/JayDDee/cpuminer-opt/releases) - Windows binary files (cpuminer-opt-x.x.x-windows.zip) and unzip the package.
- Run **cpuminer-opt** with following parameters:

```
cpuminer-sse2.exe -a yescryptr16 -o stratum+tcp://pool.litecoineco.net:3333 -u [YOUR WALLET ADDRESS]
```

*These are the parameters for official LitecoinEco pool, you can use [**other LitecoinEco pool**](./POOLS.md) with different parameters as well.*  
*If Windows blocks your cpuminer-opt, please disable Microsoft Security Esentials or other antivirus / antispyware software.*

### Mine LitecoinEco on Linux:

#### Build cpuminer-opt on Linux (example for Debian 8.x):

```sh
apt-get update && apt-get upgrade
apt-get install build-essential libssl-dev libcurl4-openssl-dev libjansson-dev libgmp-dev automake screen ca-certificates wget tar
wget https://github.com/JayDDee/cpuminer-opt/archive/vx.x.x.tar.gz
tar xvzf vx.x.x.tar.gz
mv cpuminer-opt-x.x.x cpuminer
cd cpuminer
./build.sh
```
*x.x.x stands for actual version of cpuminer-opt.*  
*Version 3.8.x throws some error during compilation, please use 3.7.10 instead.*  
*This example doesn't work on Debian 9.x, other Linux distributions were not tested.*

#### Run cpuminer-opt on Linux:

```sh
./cpuminer -a yescryptr16 -o stratum+tcp://pool.litecoineco.net:3333 -u [YOUR WALLET ADDRESS]
```
*These are the parameters for official LitecoinEco pool, you can use [**other LitecoinEco pool**](./POOLS.md) with different parameters as well.*

### Mine LitecoinEco on macOS:
- Download and install the latest version of [**XQuartz**](https://www.xquartz.org/)
- Download and install the latest stable version of [**Wine**](https://dl.winehq.org/wine-builds/macosx/download.html)
- Download and unpack the latest version of [**cpuminer-opt**](https://github.com/JayDDee/cpuminer-opt/releases) for Windows
- Run **cpuminer-sse2.exe** with parameters: **-a yescryptr16 -o stratum+tcp://pool.litecoineco.net:3333 -u [YOUR WALLET ADDRESS]** under **Wine**

*These are the parameters for official LitecoinEco pool, you can use [**other LitecoinEco pool**](./POOLS.md) with different parameters as well.*  
***LitecoinEco GUI miner** for Windows might be working on macOS under Wine too (with **wine-mono** extension), but it was not tested yet.*

### Mine LitecoinEco on Android:

- Download and install [**AA Miner from Google Play**](https://play.google.com/store/apps/details?id=com.aaminer.miner)
- Run AA Miner
- Set algorithm to **yescryptr16**
- Pool address: **stratum+tcp://pool.litecoineco.net:3333** (or any other pool address)
- User: [YOUR WALLET ADDRESS]
- Pass: nothing or "x"
- Tap on **Start mining**

## Solo mining
- Close your LitecoinEco Core wallet if still running
- Create **litecoineco.conf** file in your LitecoinEco data directory if not exists

Default data location:

Operating system | Location
---------------- | --------
Windows | %APPDATA%\LitecoinEco
Linux: | ~/.litecoineco/
macOS: | ~/Library/Application Support/LitecoinEco/

- Insert these lines to **litecoineco.conf** file and then save it:

```
server=1
rpcuser=YOUR_USER_NAME
rpcpassword=YOUR_PASSWORD
rpcport=YOUR_PORT_NUMBER
```

- Run LitecoinEco Core wallet
- Download [**cpuminer-opt**](https://github.com/JayDDee/cpuminer-opt/releases) binaries or build it from sources.
- Run **cpuminer-opt** with following parameters:

On Windows:
```
cpuminer-sse2.exe -a yescryptr16 -o http://127.0.0.1:YOUR_PORT_NUMBER -u YOUR_USER_NAME -p YOUR_PASSWORD --coinbase-addr=YOUR_WALLET_ADDRESS
```

On Linux:
```
./cpuminer -a yescryptr16 -o http://127.0.0.1:YOUR_PORT_NUMBER -u YOUR_USER_NAME -p YOUR_PASSWORD --coinbase-addr=YOUR_WALLET_ADDRESS
```

## List of mining pools
Please see [**POOLS.md**](./POOLS.md) file.

## Hashrate benchmarks
Please see [**HASHRATE.md**](./HASHRATE.md) file.
