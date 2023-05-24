---
description: Zero-Intermediate-Liquidity Market Maker
---

# 👽 ZILMM

​​A Zero-Intermediate-Liquidity Market Maker, or ZILMM, is a specific form of AMM enabled by money streams that requires zero intermediate liquidity. **This means that the total value locked by ZILMMs is zero**. Instead of using locked pools of liquidity, liquidity for swaps is sourced instantaneously by incoming flows.

This logic requires some changes to the Superfluid Protocol, which is currently being implemented in the upcoming Flow Distribution Agreement, and is scheduled for release later this year. This means money streams can be distributed to more than two parties in 0(1) computational complexity, so the gas cost is bounded.

## How is liquidity sourced?

Liquidity is derived from liquidity providers as streams. When the streams enter the pool, instead of being deposited and locked, the liquidity is split between traders swapping tokens. The remaining proportion is routed back to the liquidity provider. An interesting feature of Aqueduct's design is that swaps are also treated as liquidity, thus contributing to the liquidity depth, and in theory, could lead to new fee models where user fees approach 0%.

## _Reactiveness_

Streaming AMMs can be described as Reactive exchanges. Reactive exchanges are types of exchanges modeled with functional reactive programming. There are three variables you can judge an exchanges _reactiveness_ on:

&#x20;             **Contribution:** does the input asset enter the exchange continuously over time?

&#x20;             **Swap:** does swap between the input and assets happen continuously over time?

&#x20;             **Distribution:** is output asset distributed continuously over time?

Aqueduct is a fully reactive exchange, which means it satisfies all three _reactiveness_ criteria. Solving for all three is critical for building a fully functioning and composable streaming AMM.
