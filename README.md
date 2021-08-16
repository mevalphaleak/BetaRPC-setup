# WARNING: THIS IS EXPERIMENTAL SOFTWARE
# BetaRPC-setup

This is a clone of https://github.com/Taichi-Network/docs/blob/master/sendPriveteTx_tutorial.md though I believe it introduces few important features which make this product more convient(faster confirmation time) and safer for end users.

## Nodes

* Europe：`https://eu.betarpc.io`
* North America：`https://us.betarpc.io`

## MetaMask integration

![](menu1.png)

![](menu2.png)


## Why BetaRPC?
Using betarpc.io provides advantages on following fronts:  
(I) Speed of transaction confirmation  
(II) Mitigating payment for failed transactions  
(III) Uncle insurance fund[EXPERIMENTAL]  
(IV) No extra fees and minimal logging  

## (I) Speed of transaction confirmation
More than 99% of ETH transactions aren't affected by MEV in any way and yet using TaiChi network you have to wait 2-4x longer and use "high" gas price for 100% of submitted transactions.  
betarpc.io approaches it on two ways:  
(A) ML model at BetaRPC predicts which transactions have to be routed privately and only does it for ~1% of affected transactions  
(B) Improved coverage: it integrates TaiChi and all MEV relays: Flashbots/Ethermine/BloxRoute/Archer/MiningDAO.  

## (II) Mitigating payment for failed transactions
Using simulation + another ML model endpoint predicts probability that transaction would fail in the block where it's included on-chain.  
If probability is too high it only uses Bundle relayers to avoid payment for failed stuff  

## (III) Uncle insurance fund
Some blocks become uncles and all transactions go into mempool.  
I'll setup a bot to fight in MEVA auctions to include BetaRPC transactions from mem-pool completely unharmed.  
This will be applied only for txs which can be negatively affected by MEV.  
Uncle insurance fund is obviously not incentive compatible and is provided as-is without any guarantees whatsoever.  
It will be funded by any MEV that doesn't negatively affect BetaRPC users in any way like back-running.  

## (IV) No extra fees and minimal logging 
Endpoint is provided completely for free  
This endpoint will not save your IP or any personally identifiable information because it's none of my business.  
I'll also spin-up otterscan(https://github.com/wmitsuda/otterscan) instance to show any pending txs

## TBD
At the moment main priority is to make this endpoint relatively stable.
Right now code quality is abysmal(it was implemented in 2 days), but I'll try to open source main logic + ML models so you can run limited version locally with your own full node. Though it's not high-pri since main audience("beta" traders) don't run their own full nodes. 
