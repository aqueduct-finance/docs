---
description: How swapping tokens work on Aqueduct's TWAMM
---

# 🌊 Swapping

## Swaps

Pools support swapping one token for another over a period of time. At a high level, every pool interaction will look like this:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-21 at 11.23.08 PM.png" alt=""><figcaption><p>Swapping Functionality on Aqueducts TWAMM</p></figcaption></figure>

For reference, ETHx and USDCx are Aqueduct pool tokens - wrapped tokens that implement additional functionality to existing ERC20 tokens. Aqueduct pool tokens are also super tokens, see:

{% embed url="https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-tokens" %}

As shown, a user will start a standard (constant flow rate) stream into the pool. The user will then immediately receive a proportionate return stream (dynamic flow rate) of the opposite token in the form of 'locked' funds on Aqueduct. Traders are able to retrieve and withdraw their swapped assets at any time throughout their trade.&#x20;

{% hint style="info" %}
Aqueduct's TWAMM does not support return streams, however, later versions are expected to include the addition of a return stream similar to the way Aqueduct's 'ZILMM' works.
{% endhint %}

The return stream will update every time Aqueduct's pool price changes. See:

{% embed url="https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-agreements/constant-flow-agreement-cfa" %}

{% embed url="https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-apps" %}

## Swap Math

Aqueduct swaps work the same as a CPAMM, except transactions take place every second over an extended period. For example, assume a pool on Aqueduct starts at 1,000 USDC and 1,000 ETH (1:1 ratio, for the sake of the example).&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2023-05-21 at 11.30.23 PM.png" alt=""><figcaption></figcaption></figure>

Let's say a trader comes along and starts swapping 10 USDCx per second in exchange for ETHx. After the first second, the pool will look like the following:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-21 at 11.34.20 PM.png" alt=""><figcaption></figcaption></figure>

After one second, we can see that the price of 1 ETHx on Aqueduct is now 1.0201 USDCx in comparison to the initial price of 1:1. Let's see what the pool looks like after five total seconds of the traders swap:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-21 at 11.37.33 PM.png" alt=""><figcaption></figcaption></figure>

After five total seconds, we can see that the price of 1 ETHx is now 1.1025 USDCx. With each second, the price of ETH is becoming higher in relation to USDC. If the pool is to stay this way without any other interactions, the trader will get continuously less ETH in return of their USDC until the end of their trade.

However, there is now an arbitrage opportunity - the price of ETH on Aqueduct is different from the going market rate of ETH. Arbitrage bots are now economically incentivized to come along and fix the price on Aqueduct, bringing the price closer to the market rate. Let's take a look at what the price of ETH looks like **one second after an arbitrageur fixes the price**:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-21 at 11.44.36 PM.png" alt=""><figcaption></figcaption></figure>

After the arbitrage is executed, the price ratio of the two assets goes back to 1:1. One second later and the price is the same as we saw in the first step.\
\
This is an extreme example - a trader is unlikely to trade any token at a rate of 10/s if there is only $1,000 of said token int he pool at any given time. However, the focal point of this example is that  arbitrage brings the trader's price back to the market rate throughout the life of the trade. This reduces the trader's price impact in the long run compared to a trade that happens atomically.

We can take a look at what this type of arbitrage means for a long term trade on Aqueduct in comparison to a long term trade on a constant product automated market maker through Aqueduct's simulation tool:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-24 at 1.20.16 AM.png" alt=""><figcaption></figcaption></figure>

In this example, we assume that the trader is trying to swap $100,000,000 worth of USDC into DAI. On Aqueduct, we assume the trade occurs over 160 hours (6.67 days) and arbitrage occurs every 15 seconds. The total liquidity for the two assets on Aqueduct is worth $2,000,000 while the total liquidity on the CPAMM is worth $2,000,000,000.&#x20;

The price impact on Aqueduct is **0.26%** while the price impact on the CPAMM is **9.09%**.

{% hint style="info" %}
The Aqueduct TWAMM simulation tool is subject to several limitations, see those [here](../simulation-tools/aqueduct-twamm-vs-cpamm-simulation.md).
{% endhint %}

Aqueduct prices assets using the ratio of liquidity of each token in the pool. We define liquidity as the total amount of a given token that is present within the pool at any given time (The exact way any other AMMs pools work). Pool ratios and the total liquidity of each token in a token pair are subject to change every second as traders swap on the liquidity.

$$
flow_{B,out} =10_{A,in}\cdot\frac{1000_{B,in}}{510_{A,in}}
$$

**'Returning Streams'** are not indicative of a trader's cumulative output. Funds are locked within the pool contract until the trader chooses to withdraw them, which is fully permissible at any point during or after the user's trade.
