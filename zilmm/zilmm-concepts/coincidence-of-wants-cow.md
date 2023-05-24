---
description: Aqueduct supports automated settlement of coincidence of wants, on-chain.
---

# 💫 Coincidence of Wants (CoW)

Coincidence of wants (CoW) are automatically settled completely on-chain on Aqueduct. Two users swapping in the opposite direction can benefit from having zero intermediate liquidity between the two, meaning the pool is no longer needed in order to facilitate the traders' swaps. In this case, traders do not pay a fee to liquidity providers - the only fee taken will be the protocol fee.

Aqueduct supports "one-dimensional" CoW swaps which differs from the multi-dimensional settlement offered by CoW Swap. Coincidence of wants on Aqueduct can be simply visualized as is  in the image below:

<figure><img src="../../.gitbook/assets/Screenshot 2023-05-23 at 12.00.02 PM.png" alt=""><figcaption><p>Francesco and Victoria trading amongst themselves, on-chain</p></figcaption></figure>

Two traders swapping in the opposite direction will also have little to no effect on the pool price (assuming a similar flow rate), the two trades cancel out the affect on the pool every second. The affect of the on-chain settlement of coincidence of wants is that traders can benefit from a reduction in fees distributed to liquidity providers. Pair this fact with decentralized aggregation and traders now get to retain a majority of their token value over time. On Aqueduct, swappers get the benefit of liquidity sourced across DeFi when they need it and on-chain CoWs when they don't.

We can easily visualize coincidence of wants on Aqueduct through our pool simulation tool - let's assume two traders wan't to trade USDC and ETH with a matching flow rate of 10 per second.

{% hint style="info" %}
We are assuming ETH and USDC are 1:1 for the sake of the example, these rates are not an indication of current market conditions.
{% endhint %}

<figure><img src="../../.gitbook/assets/Screenshot 2023-05-19 at 10.23.16 PM.png" alt=""><figcaption><p>Two traders swapping 1:1 tokens with the same flow rate</p></figcaption></figure>

After a few seconds of simulated swapping, we can see that the pool price has remained the same. The two traders are getting equal output of their each respective tokens, CoW is achieved on-chain with no pool tokens necessary.\


<figure><img src="../../.gitbook/assets/Screenshot 2023-05-19 at 10.22.22 PM.png" alt=""><figcaption><p>Trader one and Trader two output, CoW after a few seconds on Aqueduct</p></figcaption></figure>

You can check out the pool simulator [here](https://twamm.aqueduct.fi/).
