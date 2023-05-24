---
description: Aqueduct supports automated settlement of coincidence of wants, on-chain.
---

# 💫 Coincidence of Wants (CoW)

### What are coincidence of wants (CoWs)?

Traditionally, CoWs is a term used in economics to describe a situation where two parties are willing to exchange goods or services because they have complementary desires or needs. For example, if Person A has apples and wants oranges, while Person B has oranges and wants apples, a coincidence of wants occurs, enabling a trade to take place.

Coincidence of wants in DeFi works on a similar level, where one person is trading token A for token B and another person is trading token B for token A. The current CoW implementations settles these types of situational trades through off-chain protocols. Before now, the settlement of coincidence of wants has not been solved in an on-chain implementation.

### Settlement of CoWs on Aqueduct

Coincidence of wants (CoW) are automatically settled with Aqueduct, entirely on-chain. Two users swapping in the opposite direction can benefit from having zero intermediate liquidity between the two, meaning the pool is no longer needed in order to facilitate the traders swaps. In this case, traders will pay a reduced fee to liquidity providers.

Aqueduct supports "one-dimensional" CoW swaps which differs from the multi-dimensional settlement offered by CoW Swap. Coincidence of wants on Aqueduct can be simply visualized as is  in the image below:

<figure><img src="../../.gitbook/assets/Screenshot 2023-05-19 at 10.10.24 PM.png" alt=""><figcaption><p>Francesco and Soleil trading amongst themselves, on-chain through Aqueduct</p></figcaption></figure>

Two traders swapping in the opposite direction will also have little to no effect on the pool price (assuming a similar flow rate), the two trades cancel out the effect on the pool every second. The effect of the on-chain settlement of coincidence of wants is that traders can benefit from a reduction in fees distributed to liquidity providers. Pair this fact with decentralized aggregation and traders now get to retain a majority of their token value over time. On Aqueduct, swappers get the benefit of liquidity sourced across DeFi when they need it and on-chain CoWs when they don't.

We can easily visualize coincidence of wants on Aqueduct through our pool simulation tool - let's assume two traders wan't to trade USDC and ETH with a matching flow rate of 10 per second.

{% hint style="info" %}
We are assuming ETH and USDC are 1:1 for the sake of the example, these rates are not an indication of current market conditions.
{% endhint %}

<figure><img src="../../.gitbook/assets/Screenshot 2023-05-19 at 10.23.16 PM.png" alt=""><figcaption><p>Two traders swapping 1:1 tokens with the same flow rate</p></figcaption></figure>

After a few seconds of simulated swapping, we can see that the pool price has remained the same. The two traders are getting equal output of their each respective tokens, perfect settlement of the CoW is achieved on-chain, with no intermediate liquidity.\


<figure><img src="../../.gitbook/assets/Screenshot 2023-05-19 at 10.22.22 PM.png" alt=""><figcaption><p>Trader one and Trader two output, CoW after a few seconds on Aqueduct</p></figcaption></figure>

You can check out the pool simulator [here](https://twamm.aqueduct.fi/).
