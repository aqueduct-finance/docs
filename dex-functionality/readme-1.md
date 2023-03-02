---
description: How swapping tokens work on Aqueduct
---

# 🌊 Swapping

## Swaps

Pools support swapping one token for another over a period of time. At a high level, every pool interaction will look like this:

![](<../.gitbook/assets/Screenshot 2022-08-15 at 9.10.48 PM.png>)

For reference, ETHxp and USDCxp are Aqueduct pool tokens - wrapped tokens that implement additional functionality to existing erc20 tokens. Aqueduct pool tokens are also super tokens, see:

{% embed url="https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-tokens" %}

As shown, a user will start a standard (static flow rate) stream into the pool. The user will then immediately receive a proportionate return stream (dynamic flow rate) of the opposite token. That return stream will update every time Aqueduct's pool price changes. See:

{% embed url="https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-agreements/constant-flow-agreement-cfa" %}

{% embed url="https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-apps" %}

## Swap Math

Let's take a look under the hood at how that outgoing stream is actually priced:

![](<../.gitbook/assets/Screenshot 2022-08-15 at 9.34.10 PM.png>)

Aqueduct prices assets using the ratio of liquidity of each token in the pool. We define liquidity as the total amount of a given token that is being streamed into the pool per second. The above diagram shows that 500 token A and 1000 token B are already being streamed every second into the pool.

$$
flow_{B,out} =10_{A,in}\cdot\frac{1000_{B,in}}{510_{A,in}}
$$

Now, let's see what would happen if another user comes along and sways the price by making a large swap:

![](<../.gitbook/assets/Screenshot 2022-08-15 at 9.54.09 PM.png>)

Trader 2 streams in a large amount of token B and receives a proportionate amount of token A based on the new ratio of liquidity. At the same time, the first trader's outgoing stream is also updated (the old flow rate is still preserved for the amount of time it was in effect).
