---
description: The key differentiator's of Aqueduct's TWAMM
---

# 🔑 Key Features (TWAMM)

## A New type of AMM

Aqueduct is a Time-Weighted Automated Market Maker (TWAMM). This is a novel design that hopes to unlock new use-cases for DeFi, and offer significant capital efficiency improvements over other AMM designs.

### Decentralized Aggregator

Aqueduct can operate on orders of magnitude less locked liquidity than the average AMM. Since Aqueduct swaps take place over time, arbitragers have the opportunity to fix pool ratios throughout the life of someone's trade. The liquidity used to fix the pool ratio can be sourced from anywhere in DeFi, benefiting the arbitrager through economic incentive and benefiting the trader by reducing their price impact.

<figure><img src="../.gitbook/assets/Screenshot 2023-05-24 at 1.36.31 AM.png" alt=""><figcaption><p>Arbitragers interacting with an Aqueduct pool</p></figcaption></figure>

Because arbitragers are coming in to fix the pool price throughout the duration of the user's trade, the total price impact of the swap has the possibility of being significantly less than on the average AMM. This shows some similarities to other aggregators currently on the market, however, Aqueduct's aggregation is done completely on-chain.

### On-Chain Settlement of Coincidence of Wants (CoW)

Aqueduct supports the settlement of coincidence of wants without any off-chain component. Traders who are trading in the opposite direction can benefit from each other by essentially swapping with each other without the help of the pool. Traders who end up in this situation will benefit from a reduced fee as the need from LPs no longer becomes a necessity. Through automated settlement of Coincidence of Wants along with reduced price impact from decentralized aggregation, traders will get to retain the most possible value of their tokens by trading over time.

### TWAP Trades

The most common execution of large orders comes in the form of TWAP trades, the main purpose being they have a reduced effect on the total market price. Aqueduct swaps take place on-chain, every second. Traders on Aqueduct will get the perfect TWAP through our TWAMM while benefiting from the most efficient price execution on the market.
