---
description: How arbitrage works on Aqueduct's TWAMM
---

# 💵 Arbitrage

In order to facilitate efficient price discovery, Aqueduct will rely on arbitrageurs to exploit price discrepancies across Aqueduct’s pools and other money markets. Arbitrageurs are the core driver behind Aqueduct's TWAMM model as a decentralized aggregator.

Arbitrage on Aqueduct's TWAMM is discoverable in the same way as any other AMM. Aqueduct provides atomic swapping abilities within its TWAMM, therefore arbitrageurs can act upon price discrepancies on Aqueduct and other markets by swapping discretely.

## Arbitrage example

The diagram below represents the total balances of token A and token B and the relationship between the two assets. Let's assume the two assets are priced 1:1:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-22 at 2.00.56 AM (1).png" alt=""><figcaption><p>1:1 asset ratio on Aqueduct (Constant Product Formula)</p></figcaption></figure>

Consider an example with two assets, asset A and asset B, with a fair market value of 1 A = 1 B. Given flow-rates of RA = 9 and RB = 10 each second into the pool, an arbitrage opportunity would be created. After some time has passed since the beginning of the swap, the pool ratio now looks like the diagram below:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-22 at 2.00.03 AM.png" alt=""><figcaption><p>Offset Asset Ratio</p></figcaption></figure>

Thus, an arbitrage opportunity is created. In order to bring the prices on Aqueduct back into alignment with fair market value, an arbitrageur can atomically swap asset A for asset B within the Aqueduct pool. With the maximum extraction of value from the arbitrage opportunity, assuming a 1:1 market rate, the pool would go back to its initial state right after an arbitrage:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-22 at 2.00.56 AM.png" alt=""><figcaption><p>Back to 1:1 after arbitrage</p></figcaption></figure>

Under this model, arbitrageurs can source liquidity from across DeFi in order to fix the price on Aqueduct. Because this arbitrage has occurred during a users trade, the user is benefiting from arbitrage throughout their trade.&#x20;

Arbitrageurs are inherently the main price drivers on Aqueduct outside of swappers, as is the same with any CPAMM. Since liquidity can be sourced from anywhere and the user benefits from a more accurate rate, Aqueduct's TWAMM can be described as a decentralized aggregator.
