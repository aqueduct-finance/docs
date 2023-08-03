# AqueductV1Pair

Similar to the factory, AqueductV1Pair retains a lot of functionality from Uniswap V2's [pair](https://docs.uniswap.org/contracts/v2/reference/smart-contracts/pair) contract. In this case, significant modifications were made to the reserve calculations to correctly handle time-based swaps.



## What stays the same

* Providing liquidity keeps the same interface. LPs call `mint()` (or a high-level wrapper function) to create a position and `burn()` to remove their position.&#x20;
  * The only difference here is that the pair's reserves need to be dynamically calculated based on incoming streaming swaps and the time difference between blocks
  * Just like in Uniswap V2, LPs are rewarded pro-rata because fees from trades are added directly to the reserves
* For sake of security, the `swap()` function is also largely unchanged
  * The pair's dynamic reserves are also updated in the swap function
  * It is also now permissioned to only be called by the AqueductV1Auction contract
  * In order to give flexibility to the auction contract, the `swap()` function no longer natively charges a fee on trades, delegating that responsibility to the auction



## What was added

* A new interface for time-based swaps
  * Each AqueductV1Pair is registered as a super app in the Superfluid protocol, meaning it contains hooks that atomically respond to stream creation, updates, and deletion. Superfluid calls these '[callbacks](https://docs.superfluid.finance/superfluid/developers/super-apps/super-app-callbacks)'
  * For example, the callback below is called when a stream is sent to the pair's address. With that, data is passed in that identifies the token, user, etc...

```solidity
function afterAgreementCreated(
    ISuperToken _superToken,
    address, //_agreementClass,
    bytes32, //_agreementId
    bytes calldata _agreementData,
    bytes calldata _cbdata,
    bytes calldata _ctx
) external override onlyHost returns (bytes memory newCtx) {
    _handleCallback(_superToken, _agreementData, _cbdata);
    newCtx = _ctx;
}
```

* Time-weighted reserves
  * Streamed balances are calculated based on each block's timestamp, meaning that the streams are effectively running between blocks
  * In the same way, each pair's reserves update dynamically based on block timestamps, meaning that swaps are also effectively running between blocks
  * For sake of simplicity, our pools use an approximation of the formulae derived in [Paradigm's twamm paper](https://www.paradigm.xyz/2021/07/twamm)
  * Because batch output of streams is not possible today on Superfluid protocol, pairs will lock each trader's output, which can be manually collected with `retrieveFunds()` or will automatically be transferred during any future callbacks

