# AqueductV1Auction

This auction contract controls interactions with AqueductV1Pair's swap() function, which is used to make atomic/instant swaps. It is expected that when options are available for both long-term time based swaps and atomic/instant swaps, that informed traders will tend to choose an instant swap. This auction contract is designed to capture the most value from informed trades, and return the funds to liquidity providers.



## Design Considerations

* AqueductV1Auction is abstracted from AqueductV1Pair by design, such that we can make incremental improvements to the auction contract without necessarily needing to change the design of the pair
* Because arbitrage is a core component of the twamm, the auction contract is not upgradable, and the factory will be permanently paired with it
  * In the future, if incremental improvements are made to the auction contract, then a new factory will also need to be deployed, with separate pairs, and LPs will need to migrate their funds
* For sake of simplicity, version 1 is designed as a public english (increasing) auction, with an auction occurring every block
* There is strong [consensus](https://www.mechanism.org/spec/01) that Ethereum (and other evm chains) have poor censorship resistance with respect to timely inclusion of transactions
  * We expect that participants will need to give conditional tips to proposers ([eip-1559](https://eips.ethereum.org/EIPS/eip-1559)), with larger tips having a higher chance of timely inclusion
  * Given these circumstances, we set a minimum fee of 0.3% (the trader's call to placeBid() will revert if their bid is less than 0.3% of their swapAmount)
    * With this, LPs should not be worse off than LPs in a Uniswap V2 pool, with a flat fee of 0.3%
    * In the future, if we can guarantee timely inclusion for participants, then this minimum fee can be removed. This would significantly improve trade efficiency for non-volatile pairs by enabling more frequent arbitrage



## Write Operations

#### placeBid()

```solidity
function placeBid(
   address token,
   address pair,
   uint256 bid,
   uint256 swapAmount,
   uint256 deadline
) external ensure(deadline)
```

* Let's say it is block A and an arbitrageur would like to make a quick trade
  * They approve the auction contract for the token they are looking to swap and call placeBid() in block A, which instantly swap `swapAmount` of `token` and lock the output from the swap, along with the bid
  * If another arbitrageur is willing to bid higher, they can call placeBid() with that higher bid. This will reverse the swap of the first trader and send their funds back. If this trader's bid is lower, the transaction will simply revert
  * During block B or later, anyone can call the permissionless `executeWinningBid()` function



#### executeWinningBid()

```solidity
function executeWinningBid(address pair) public
```

* Transfers the winning swap amount to the winner of the previous auction
* Also sends the winning bid from to the pair contract
  * This will reward LPs, as the bid is added to the reserves.
