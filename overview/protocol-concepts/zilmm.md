---
description: Zero-Intermediate-Liquidity Market Maker
---

# ZILMM

A Zero-Intermediate-Liquidity Market Maker, or ZILMM, is a specific form of AMM enabled by money streams that requires zero intermediate liquidity. This means that the total value locked by ZILMMs is zero. Instead of using locked pools of liquidity, liquidity for swaps is sourced instantaneously by incoming flows

Streaming AMMs can be described as Reactive exchanges. Reactive exchanges are types of exchanges modeled with functional reactive programming\[3]. There are three variables you can judge an exchanges reactiveness on:&#x20;



**Contribution**: does the input asset enter the exchange continuously over time?&#x20;

**Swap**: does swap between the input and assets happen continuously over time?&#x20;

**Distribution**: is output asset distributed continuously over time?&#x20;



Aqueduct is a fully reactive exchange, which means it satisfies all three reactiveness criteria. Solving for all three is critical for building a fully functioning and composable streaming AMM.
