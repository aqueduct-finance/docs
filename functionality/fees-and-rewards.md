---
description: How fees work on Aqueduct's TWAMM
---

# 💰 Fees

Aqueduct pays out rewards to LPs in order to incentivize liquidity contributions.&#x20;

## Swaps

Let's say that our pool now has a 0.3% fee:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-22 at 12.35.58 AM.png" alt=""><figcaption><p>Fee Visualization on Aqueducts TWAMM</p></figcaption></figure>

{% hint style="info" %}
This fee % is only an example, actual fee percentages are likely to change throughout the life of the protocol.
{% endhint %}

The total amount taken through the fee on Aqueduct will change every second as prices deviate from the market rate in-between arbitrage executions. Regardless, liquidity providers are paid out fees from swaps every second

## LP + Swap

An LP is rewarded based on their reward percentage and the size of their liquidity contribution. If a given LP has a reward percentage of 1 and controls all liquidity in the pool, then they would receive all of the fees paid by traders. Let's take the LP example from earlier and now introduce a 10% fee:

![](<../.gitbook/assets/Screenshot 2022-08-16 at 12.07.56 AM.png>)

Because the LP started their streams before the trader, their reward percentage is recorded as 1. We can calculate the amount of fees paid in token A by the trader as follows:

$$
fees_A=5_{B,in}\cdot\frac{100_{A,in}}{205_{B,in}}\cdot0.1
$$

Because the LP is providing all liquidity for token A, they get the entirety of those fees. We can calculate the LP's return stream of token A as follows:

$$
flow_{A,out}=\bigg(200_{B,in}\cdot\frac{100_{A,in}}{205_{B,in}}\bigg)+fees_A
$$
