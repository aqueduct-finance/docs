---
description: Aqueduct's TWAMM serves as a fully decentralized aggregator.
---

# ✨ Decentralized Aggregation

Aqueduct's Time-Weighted Automated Market Maker can be considered a decentralized aggregator due to its unique characteristics and functionality of executing trades over time. The aspect that makes the TWAMM a decentralized aggregator is the ability to leverage arbitrageurs to fix the pool price throughout the duration of a user's trade, thereby reducing price impact.

Just like in a traditional AMM, arbitrageurs play a critical role in regulating the pool price on Aqueduct's TWAMM by continuously monitoring the market for price discrepancies across different liquidity sources in DeFi in comparison to the TWAMM price. Arbitrageurs capitalize on these price differences by sourcing liquidity from various DeFi protocols and executing trades to maintain the target price on Aqueduct. The end result is a constant relationship between traders on Aqueduct and the arbitrageur, where the price on Aqueduct is brought back to the market rate every time there is economic incentive to do so.

<figure><img src="../../.gitbook/assets/Screenshot 2023-05-24 at 1.36.31 AM.png" alt=""><figcaption><p>Arbitrageurs sourcing liquidity from various sources to fix the TWAMM price</p></figcaption></figure>

By relying on arbitrageurs to source liquidity from across DeFi, Aqueduct acts as a decentralized aggregator.

## How do normal aggregators work?

DEX aggregators like CoW Swap and 1inch are platforms that aggregate liquidity from various DEXs and route trades to achieve the best trade execution among the connected exchanges. These aggregators use a combination of on-chain and off-chain protocols to source liquidity, compare prices, and execute trades on behalf of the user.

Off-chain protocols enable the aggregator to compare prices and assess trading costs, including transaction fees and slippage, associated with each DEX. By considering these factors, the aggregator determines the most favorable trade execution strategy for the user.

With this off-chain implementation, users are forced to trust centralized infrastructure employed by the aggregator if they are to take advantage of the presented benefits. The core issue with this model is that the functionality of these aggregators are not executable on-chain, and they break protocol composability by moving computation off-chain. DEX aggregators are also not perfectly optimal for large trades, considering the trade still must be executed across a select few exchanges.

## Aqueduct TWAMM - Decentralized Aggregator

Instead of being limited to a single liquidity source, Aqueduct's TWAMM can tap into multiple decentralized exchanges, lending protocols, and other DeFi platforms through arbitrageurs to fulfill liquidity requirements. This decentralized aggregation of liquidity allows Aqueduct to provide competitive pricing and deeper liquidity.

The decentralized aggregation aspect of Aqueduct brings several benefits to trading over time. Firstly, it enables traders to access liquidity from a broader range of sources, reducing price impact and improving slippage. Additionally, by spreading the liquidity across various protocols, Aqueduct helps mitigate the risk associated with single-platform concentration, promoting a more resilient market infrastructure.

The decentralized nature of the TWAMM aligns with the core principles of DeFi, such as trustlessness and censorship resistance. By sourcing liquidity from decentralized sources, the TWAMM eliminates the need for centralized intermediaries and reduces counterparty risk. This enhances the security and resilience of the trading process, fostering greater user trust in the DeFi ecosystem.

## End Result for the Trader

Trade execution on a CPAMM, especially for large orders, has an immediate impact on the pool's reserves and results in increased price impact. After the fact, arbitrageurs come along and fix the pool price - having no effect on the trader's output. Since swaps on Aqueduct take place over time, arbitrageurs have the opportunity to fix the pool price throughout the life of a trade. This in turn reduces the price impact of the trader's output by constantly bringing the price back to the market rate.

This has benefits for any trade that gets executed on Aqueduct, but it's especially important for large trades. See [Iceberg Orders](../../use-cases/iceberg-orders.md) and [DAO Treasury](../../use-cases/dao-treasury.md).\
\
Refer to the TWAMM paper by Paradigm for more information on this topic: [https://www.paradigm.xyz/2021/07/twamm#executing-large-orders-on-current-amms](https://www.paradigm.xyz/2021/07/twamm#executing-large-orders-on-current-amms)
