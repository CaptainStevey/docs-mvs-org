title: Guide to PoS and MST mining 
comments: true
---

# Download & Install v0.9.0 MPC1
Please refer to the [wallet](https://mvs.org/wallet.html) page to download and install the latest wallet.

# PoS Mining

## How to start PoS mining
Please follow the below steps to start PoS mining:
1. Register an avatar.
2. Lock at least 1000 `ETP` by calling `lock` with the avatar. The minimum lock height range is 100000.
3. The avatar should hold at least one `UTXO` which has at least 1000 `ETP` and over 1000 height maturity. 
4. `startmining` with option `-c pos`.

## Tips
It is easy to mine PoS blocks for an avatar that has many `UTXO`s which have at least 1000 `ETP`.

## Operations on fullnode wallet 
![Operations on fullnode wallet](/images/mining/en/pos_mst_mining_overview.png)

# MST Mining

## How to start MST mining

### MST issuer
The `MST` issuer should specify the `MST` mining subsidy parameters(`--subsidy`) when the `MST` is initially issued to allow it to be mined.

The format of `--subsidy` parameter is `initial:unit32,interval:unit32,base:float`. 

`MST` mining reword is calculated by：`initial * pow(base, (block_height/interval))`.

#### Example
issue:
`./mvs-cli issue testacc testacc MST.MST.TEST -s "initial:300000000,interval:500000,base:0.95"`

`MST` mining reword = 300000000 * pow(0.95, (Current block height - Height when MST issued) / 500000).

#### Operations on fullnode wallet
![Operations on fullnode wallet ](/images/mining/en/mst_mining_create_asset.png)

### Miner
To start mining the command `startmining` needs to be entered along with the option `--symbol` and the symbol of the `MST` to be mined.
