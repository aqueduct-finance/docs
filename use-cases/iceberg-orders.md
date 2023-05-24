---
description: Aqueduct is the best place to execute large orders.
---

# 💰 Iceberg Orders

Currently, the best way to swap large amounts of tokens is to break the total sum into smaller sub-orders - executing these smaller sub-orders manually over time. This is commonly known as a TWAP in DeFi and regular finance, and it's used to reduce the impact a single trade has on the entire market.

This type of trade is inefficient to execute on-chain as gas fees are likely to pile up the more you break up your trade. On the other hand, if you break the trade into larger chunks, you are likely going to suffer from larger amounts of slippage.

Aqueduct solves this problem for traders looking to swap large amounts of tokens by breaking the trade up into a 'flow-rate,' the per-second rate to which tokens are swapped. Traders can choose however long they want their trade to be executed through, in which a piece of the total trade will be swapped every second throughout that period.

This completely automates the process of manually executing a large order for traders.

### Reduced Price Impact (Decentralized Aggregation)

Since swaps on Aqueduct take place over time, the impact a user's trade has on the price of a token is not instant. Therefore, a user's effect on the pool price can be fixed during the user's trade, thus bringing the trader's price back to the market rate.&#x20;

The 'fixers' in this case are arbitragers who source liquidity from across DeFi to fix the price on Aqueduct. The end result of this trade/arbitrage relationship is an economically incentivized arbitrageur looking to capitalize on differences in market rates and a trader who's overall price impact has been reduced due to the arbitrager's access to liquidity across DeFi.&#x20;

To help visualize this process, we built a simulation tool to help show the impact an arbitrager has on a users overall trade.

First, let's assume the market rate of ETH/USDC is 1:1 and a trader want's to swap 100 USDC a second into ETH.

<figure><img src="../.gitbook/assets/Screenshot 2023-05-19 at 10.41.17 AM.png" alt=""><figcaption><p>1:1 ETH/USDC Pool, trading 100 USDC per second</p></figcaption></figure>

{% hint style="info" %}
This is simply an example of how Aqueduct works as a decentralized aggregator, pool ratios are not meant to reflect actual market rates.
{% endhint %}

Lets simulate the first few seconds of the users swap:\


<figure><img src="../.gitbook/assets/Screenshot 2023-05-19 at 10.45.05 AM.png" alt=""><figcaption></figcaption></figure>

The trader has now streamed 130 USDC into the pool and has gotten a return of 115 ETH within that time frame. The price of ETH on Aqueduct is now .277 USDC different than the market rate, therefore, an arbitrage opportunity presents itself.\
\
In this case, an arbitrage bot will see this price discrepancy and fix the price on Aqueduct - once again, because it's economically incentivized to do so. Let's assume in this case that the first arbitrageur takes full control of the opportunity and brings the price right back to 1:1.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2023-05-19 at 10.58.07 AM.png" alt=""><figcaption><p>Arbitrageur fixes the price</p></figcaption></figure>

Because of the arbitrageur fixed the price, the ratio between the two was brought back to 1:1. The trader is now trading at the market rate.

This example is used to show an extreme case in which the pool only has $2,000 worth of liquidity and a trader is swapping $100 worth of USDC every second. Actual implementation will likely see more liquidity and lower flow rates, meaning the price gets affected at a much slower rate.

In either case, the arbitrageur will still do their job in fixing the pool price. Ensuring that the trader is swapping at the actual market rate and reducing price impact.

### Gas Efficiency

The generic implementation of the TWAMM suffers from the problem of gas inefficiencies through which the period where orders can expire. If orders are to expire every block, the gas efficiency of the TWAMM will be unreasonable - washing away all use cases for trading over time. However, current preferred implementation of the TWAMM sets a fixed order expiry. For example, a trade of 100 ETH will only be eligible to expire every 250 blocks or so, the exact block interval being dependent on the implementation. Gas becomes a problem during periods of inactivity, as computing the effect of trades is linear in complexity with respect to time. This means if a pool is inactive for many block intervals, the next trader will pay an enormous gas fee, and once the gas usage of the full computation exceeds the gas allocation for an entire block, the pool will become unusable.

The traditional TWAP is even worse, as the amount of sub-orders an order is split into has a direct correlation to the total amount of gas a user is going to pay for the whole trade. For larger sub-orders, less overall gas costs but increased slippage. For smaller sub-orders, less slippage but an increased overall gas cost.

Aqueduct improves upon both of these issues by requiring two separate transactions for any trade at any length, both of which have a fixed gas cost. Meaning that the duration of the user's trade and any periods of inactivity have no affect on the amount of gas they need to pay. This allows Aqueduct to avoid using block intervals all together - orders can expire within any block and users only pay gas for the start and end of their transaction.



