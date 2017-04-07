Make Punk great again
=====================================


https://cyberpunk.com


Punkcoin Core integration/staging tree
------------



Forking
------------

Follow the guide:
https://vcoin-project.github.io/cloning-litecoin/

4a. ~~Download and extract the Litecoin source~~

4b. ~~Copy and Replace Litecoin~~
```
grep -rl 'litecoin-project' ./ | xargs sed -i 's/litecoin-project/btcpunk/g'
grep -rl 'litecoin' ./ | xargs sed -i 's/litecoin/isicoin/g'
grep -rl 'Litecoin' ./ | xargs sed -i 's/Litecoin/Isicoin/g'
grep -rl 'LITECOIN' ./ | xargs sed -i 's/LITECOIN/ISICOIN/g'
grep -rl 'lite' ./ | xargs sed -i 's/lite/isi/g'
grep -rl 'LITE' ./ | xargs sed -i 's/LITE/ISI/g'
grep -rl 'Lite' ./ | xargs sed -i 's/Lite/Isi/g'
```
4c. ~~Copy and Replace LTC~~
```
grep -rl 'ltc' ./ | xargs sed -i 's/ltc/isi/g'
grep -rl 'LTC' ./ | xargs sed -i 's/LTC/ISI/g'
grep -rl 'Ltc' ./ | xargs sed -i 's/Ltc/Isi/g'
```

4d. Change rpc and port numbers
```
Litecoin
main port 9333 
testnet 19333
rpcport 9332
regtest 19332
```
```
Punkcoin
main port 10333 
testnet 11333
rpcport 10332
regtest 11332
```
4e. Change starting letter for addresses.
```
In this case we change the 48 to 28, therefore all addresses will start with “C”.
```
4f. Update client version number.
```
configure.ac:
define(_CLIENT_VERSION_MAJOR, 1)
define(_CLIENT_VERSION_MINOR, 0)
define(_CLIENT_VERSION_REVISION, 0)
define(_CLIENT_VERSION_BUILD, 0)
define(_COPYRIGHT_YEAR, 2017)

src/clientversion.h:
#define CLIENT_VERSION_MAJOR 0
#define CLIENT_VERSION_MINOR 13
#define CLIENT_VERSION_REVISION 3
#define CLIENT_VERSION_BUILD 0
#define COPYRIGHT_YEAR 2017
```
4g. Change Litecoin example addresses to Clonecoin Addresses.
```
Default litecoin address: Ler4HNAEfwYhBmGXcFP2Po1NpRUEiK8km2
```
4h. Change char pchMessageStart and ParseHex.
```
```
4i. Change alert keys.
```
src/alert.cpp
static const char* pszMainKey = "040155710fa689ad5023690c80f3a49c8f13f8d45b8c857fbcbc8bc4a8e4d3eb4b10f4d4604fa08dce601aaf0f470216fe1b51850b4acf21b179c45070ac7b03a9";
static const char* pszTestKey = "04305590343f91cc401d56d68b123028bf52e5fca1939df127f63c6467cdf9c8e2c14b61104cf817d0b780da337893ecc4aaff1309e536162dabbdb45200ca2b0a";
 ```
4j. Remove Merkel root and Genesis Block.
 ``` 
 ```
4k. Remove Nonce and testnet genesis.
 ```
  ```
4l. Add Epochtime and Timestamp.
 ```
./src/chainparams.cpp:
const char* pszTimestamp = "In 1932 the editor Mario Nerbini decided to open a new weekly newspaper for kids, containing illustrated tales with Mickey Mouse.";
...
genesis = CreateGenesisBlock(1483228800, 1234567890, 0x1e0ffff0, 1, 100 * COIN);
  ```
4m. Fixing the checkpoints.
```
./src/chainparams.cpp:
 checkpointData = (CCheckpointData) {
                boost::assign::map_list_of
                        (  0, uint256("0x"))
        };
  ```
4n. Change max money supply and coinbase maturity.
```
./src/amount.cpp:
static const CAmount MAX_MONEY = 999000000 * COIN;
./consensus/consensus.h:
static const int COINBASE_MATURITY = 10;
```
4o. Change block times from 2.5 minutes to 30 seconds.
```
./src/chainparams.cpp:
consensus.nPowTargetSpacing = 1 * 30;
```
4p. Change re-targeting from the ridiculous 2.5 days to every 5 minutes.
```
./src/chainparams.cpp:
consensus.nPowTargetTimespan = 10 * 30;
```
4q. Add premine and change block rewards.
```
./src/chainparams.cpp:
genesis = CreateGenesisBlock(1483228800, 1234567890, 0x1e0ffff0, 1, 100 * COIN);
```
4r. Update Images.
```
convert -resize 16 -background transparent -gravity center -crop 16x16+0+0 troll.png -flatten -colors 256 troll.ico
cp /Downloads/troll.png qt/res/icons/bitcoin.png 
cp /Downloads/troll.ico qt/res/icons/bitcoin.ico 
```
4s. Update Seed node-


License
-------

Punkcoin Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.
