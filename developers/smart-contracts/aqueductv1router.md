# AqueductV1Router

Aqueduct V1 inherits a nearly unmodified [router](https://docs.uniswap.org/contracts/v2/reference/smart-contracts/router-02) contract from Uniswap V2. There are two small differences:

* Because AqueductV1Auction handles instant/atomic swaps, those functions were removed from the router, leaving only functions related to liquidity provision
* While this isn't a change to the router, it is worth noting that the router will call `pair.getReserves()` to make calculations that involve the target pair's reserves. AqueductV1Pair has an updated `getReserves()` function that will calculate the dynamic reserves, rather than just returning the reserves as of the last state change
