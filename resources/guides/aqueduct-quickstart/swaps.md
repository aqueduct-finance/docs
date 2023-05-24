---
description: Initiate a swap using our demo
---

# Swaps

**IMPORTANT**: Because Superfluid has not released their [Flow Distribution Agreement (FDA)](https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-agreements/streaming-distributions-coming-soon), which contains the logic needed for Aqueduct to be composable with the rest of the Superfluid ecosystem, we have temporarily built the required logic into our pool and also, a custom token. Our demo app uses a custom `SuperToken` with a modified `realTimeBalance` function. These tokens have an `xp` suffix. `x` denotes it being a SuperToken and `p` denotes pool. This is because these tokens are not composable with the rest of the real time finance ecosystem - only Aqueduct's pools.



**1.** Head to [https://demo.aqueduct.fi/](https://demo.aqueduct.fi/) and connect your wallet.

<figure><img src="../../../.gitbook/assets/Screen Recording 2022-11-28 at 21.30.42.gif" alt="Gif showing how to connect your wallet"><figcaption></figcaption></figure>

**2.** Navigate to the _"Wrap / Unwrap"_ page. Select the amount of tokens you want to upgrade and click _"Wrap"_. You'll need to approve two transactions for this action, one to approve the Aqueduct smart contracts to access your tokens, and the second to actually upgrade those tokens.

<figure><img src="../../../.gitbook/assets/Screen Recording 2022-11-28 at 22.17.27.gif" alt=""><figcaption></figcaption></figure>

**3.** Then navigate back to the _"Swap"_ page. Enter the flow-rate you want to swap the token at. You can choose a per-second flow-rate or anywhere up to per-year flow-rate. Then click on the _"Swap"_ button to initiate the swap. **Note:** _You will need to provide a small buffer to initiate the swap._

<figure><img src="../../../.gitbook/assets/Screen Recording 2022-11-28 at 22.46.04.gif" alt=""><figcaption></figcaption></figure>

**4.** Finally, visit the _"My Streams"_ page to view your active streams

<figure><img src="../../../.gitbook/assets/Screen Recording 2022-11-28 at 22.52.58.gif" alt=""><figcaption></figcaption></figure>

