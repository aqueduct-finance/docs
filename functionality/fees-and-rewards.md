---
description: How fees work on Aqueduct's ZILMM
---

# 💰 Fees (ZILMM)

Aqueduct pays out rewards to LPs in order to incentivize liquidity contributions.&#x20;



Aqueduct does not distinguish between LPs and regular swaps - instead, we calculate a static reward percentage at the start of each stream:

$$
fee_{\%}=\frac{|ratio_{user}-ratio_{pool}|}{ratio_{user}+ratio_{pool}}
$$

$$
reward_{\%}=1-fee_{\%}
$$

That fee percentage ranges from 0 to 1. For example, a trader streaming in only one token (swapping) would have a fee percentage of 1 (100%). An LP whose ratio of streams perfectly matches the pool ratio would have a fee percentage of 0. Each percentage is static and calculated at the start of a stream, meaning LPs do not need to worry about changes in the pool ratio.

## Swaps

Let's say that our pool now has a 0.5% fee:

![](<../.gitbook/assets/Screenshot 2022-08-15 at 11.52.54 PM.png>)

The user's fee percentage would be 1, meaning they pay the entirety of that 0.5% pool fee. Their outgoing flow is calculated as follows:

$$
flow_{B,out} =10_{A,in}\cdot\frac{1000_{B,in}}{510_{A,in}}\cdot 0.995
$$

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
