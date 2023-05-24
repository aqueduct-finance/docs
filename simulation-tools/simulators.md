---
description: Trading and functionality simulators for Aqueduct's TWAMM
---

# 🕹 Simulators

### TWAMM vs CPAMM Simulation

The TWAMM vs CPAMM simulation tool allows you to simulate a trade that happens on Aqueduct versus a trade that happens on a constant product automated market maker (e.g. Uniswap). The simulator is meant to show the differences in price impact between the two AMMs. Aqueduct allows traders to swap over time, whereas a CPAMM only allows for the discrete swapping of tokens. Aqueduct, at its core, is a decentralized aggregator - since swaps take place over time, arbitragers have the opportunity to source liquidity from other AMMs in order to fix the pool price on Aqueduct (and make a profit). Thus, trades on Aqueduct benefit from arbitrage because price impact is being improved every time an arbitrage bot fixes the price.

{% content-ref url="aqueduct-twamm-vs-cpamm-simulation.md" %}
[aqueduct-twamm-vs-cpamm-simulation.md](aqueduct-twamm-vs-cpamm-simulation.md)
{% endcontent-ref %}

### Aqueduct TWAMM Pool Simulation

The Aqueduct TWAMM Pool simulation tool allows you to get a real time visualization of what pools look like throughout the life of a trade. You can simulate arbitrage yourself in whatever interval you choose, in which the pool price will be back to the market rate after each arbitrage trade. You can try out this simulation tool here -> ([https://twamm.aqueduct.fi/](https://twamm.aqueduct.fi/))

{% content-ref url="twamm-pool-simulator.md" %}
[twamm-pool-simulator.md](twamm-pool-simulator.md)
{% endcontent-ref %}

### Aqueduct ZILMM Simulation Tool

The Aqueduct ZILMM Pool simulation tool allows you to get a visualization of what the reactive pool and swapping structure looks like on Aqueducts ZILMM.

{% content-ref url="zilmm-simulator.md" %}
[zilmm-simulator.md](zilmm-simulator.md)
{% endcontent-ref %}
