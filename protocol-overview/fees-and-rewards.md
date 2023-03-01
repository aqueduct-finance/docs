---
description: The trading protocol for real-time finance.
---

# 🌊 What is Aqueduct?

## Token Swaps, Powered by Money-Streams

Aqueduct is a real-time decentralized exchange that allows users to swap tokens and provide liquidity through money streams. This is done through a framework of smart contracts on Ethereum, allowing you to seamlessly swap funds from one token to another. Built on Superfluid, we inherit all of the core functionality that makes the transferring of tokens on a per second basis possible.

We currently define ourselves as two types of market makers:

****:potable\_water: **"ZILMM"** - A Zero-Intermediate-Liquidity Market Maker, or ZILMM, is a specific form of AMM enabled by money streams that requires zero intermediate liquidity. This means that the total value locked by ZILMMs is zero. Instead of using locked pools of liquidity, liquidity for swaps is sourced instantaneously by incoming flows.

****:ocean: **"TWAMM"** - A time-weighted automated maker, or TWAMM. A variation on a traditional AMM that allows traders to execute orders over a period of time. It breaks trades into infinitely many infinitely small virtual orders, and executes them against an embedded constant-product AMM over time.

Aqueduct exists as a TWAMM and a ZILMM at the same time - Zero intermediate liquidity is required, and swaps take place over time through money streams.

## A New Class of DEX

Aqueduct exists as an entirely new class of DEX in the ever evolving ecosystem that is DeFi. We are the first exchange for allow for zero intermediate liquidity, or 0 value locked - liquidity providers don't have to deposit tokens to provide liquidity. Aqueduct is also the first stream-native DEX that allows for the per second transfer of one asset to another.
