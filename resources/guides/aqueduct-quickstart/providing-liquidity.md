---
description: Provide liquidity and start earning fees
---

# Providing Liquidity

**IMPORTANT**: Because Superfluid has not released their [Flow Distribution Agreement (FDA)](https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-agreements/streaming-distributions-coming-soon), which contains the logic needed for Aqueduct to be composable with the rest of the Superfluid ecosystem, we have temporarily built the required logic into our pool and also, a custom token. Our demo app uses a custom `SuperToken` with a modified `realTimeBalance` function. These tokens have an `xp` suffix. `x` denotes it being a SuperToken and `p` denotes pool. This is because these tokens are not composable with the rest of the real time finance ecosystem - only Aqueduct's pools.

Accompanying GIFs coming soon...

1. Head to [https://demo.aqueduct.fi/](https://demo.aqueduct.fi/) and connect your wallet.
2. Navigate to the _"Wrap / Unwrap"_ page. You will need both tokens in a token pair to provide liquidity. Select the amount of tokens you want to upgrade and click _"Wrap"_. You'll need to approve two transactions for this, one to approve the Aqueduct smart contracts to access your tokens, and the second to actually upgrade those tokens. Repeat the steps again for the second token.
3. Then navigate to the _"Provide Liquidity"_ page. Enter the flow-rate you want to provide liquidity for both tokens at. You can choose a per-second flow-rate or anywhere up to per-year flow-rate. Then click on the _"Update Position"_ button to start providing liquidity. **Note:** _You will need to provide a small buffer of each token to initiate the swap._
4. Finally, visit the _"My Streams"_ page to view your active streams.
