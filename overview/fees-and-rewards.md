---
description: The trading protocol for real-time finance.
---

# 🌊 What is Aqueduct?

## Token Swaps, Powered by Money-Streams

Aqueduct is a real-time decentralized exchange that allows users to swap tokens and provide liquidity through money streams. This is done through a framework of smart contracts on Ethereum, allowing you to seamlessly swap funds from one token to another. Built on the [Superfluid Protocol](https://www.superfluid.finance/), we inherit all of the core functionality that makes the transferring of tokens on a per second basis possible.

## Underlying AMM design

Aqueduct is a completely new type of Automated Market Maker (AMM), one defined by the use of money streams, and having zero locked liquidity. At it's core, Aqueduct is a ZILMM:

****:ocean: **"ZILMM"** - A Zero-Intermediate-Liquidity Market Maker, or ZILMM, is a specific form of AMM enabled by money streams that requires zero intermediate liquidity. This means that the total value locked by ZILMMs is zero. Instead of using locked pools of liquidity, liquidity for swaps is sourced instantaneously by incoming flows. Read more about ZILMMs in our [protocol concepts section page](protocol-concepts/zilmm.md).

The design also shares some similarities with [TWAMMs](https://www.paradigm.xyz/2021/07/twamm#the-time-weighted-average-market-maker). A Time-Weighted A_verage_ Market Maker, or TWAMM, is a type of AMM that allows traders to execute orders over a period of time. It breaks trades into infinitely many infinitely small virtual orders, and executes them against an embedded constant-product AMM over time. Aqueduct permits the execution of time-weighted orders over time, but it don't execute orders against an embedded constant-product AMM. Instead, zero intermediate liquidity is required, and swaps take place over time using money streams.

## A New Class of DEX

Aqueduct exists as an entirely new class of DEX in the ever evolving ecosystem that is DeFi. We are the first exchange for allow for zero intermediate liquidity, or 0 value locked, which means liquidity providers don't have to deposit and lock up their tokens to provide liquidity. Aqueduct is also the first stream-native DEX that allows for the per second transfer of one asset to another.
