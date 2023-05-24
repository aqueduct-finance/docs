---
description: How to use and understand the Aqueduct TWAMM vs CPAMM simulation tool
---

# 🕹 Aqueduct TWAMM vs CPAMM Simulation

### What is a CPAMM?

The core principle of a CPAMM is to maintain a constant product of the reserves of two tokens in a liquidity pool. Typically, these tokens are a base token and another token that users want to trade against the base token. The more a token is bought, the higher its price becomes, and vice versa. This mechanism allows for decentralized and continuous trading on DEXs.

CPAMM was popularized by the creation of Uniswap, one of the pioneering decentralized exchanges. Uniswap introduced the concept of a CPAMM to provide liquidity and facilitate trading without the need for traditional order books.

### &#x20;What is a TWAMM?

A Time-Weighted Average Market Maker, or TWAMM, is a type of AMM that allows traders to execute orders over a period of time. It breaks trades into infinitely many infinitely small virtual orders, and executes them against an embedded AMM over time. **Aqueduct's TWAMM** permits the execution of time-weighted orders over time, executing orders against an embedded constant-product AMM.

## Simulate Swap Widget

### Pick a Swap Amount

When you first load up the simulator, you will see a 'Simulate Swap' widget with an input box for swap amount, along with two sliders. The number you put into the first input box indicates the total swap amount you want to simulate on both Aqueduct and the CPAMM.

<figure><img src="../.gitbook/assets/Screenshot 2023-05-24 at 1.52.59 AM.png" alt=""><figcaption><p>Enter a swap amount</p></figcaption></figure>

### Pick a Swap Time

The simulate swap widget includes a time slider that allows you to change the length of the simulated trade. In the example above, the simulated trade would swap $100,000,000 USDC for a token with a 1:1 market rate. The time slider is set to 168 hours, or seven days. This indicates that the total time the order will take to be completely swapped will be 168 hours. On Aqueduct, a portion of the total USDC will be swapped from USDC to DAI every second until the end of the set time slot. It's important to note that this trade will take place on the CPAMM instantly, having an immediate affect on the CPAMMs liquidity and the traders price impact.

### Pick a Time to Arbitrage

The widget also contains an arbitrage time slider which sets the time it takes during a user's swap for an arbitrager to come along and fix the price. Arbitragers will be able to trade directly against the pool in the same way made possible on any other constant product automated market maker (CPAMM). Due to arbitrage, Aqueduct acts as a decentralized aggregator. Throughout the life of a user's swap, arbitragers source liquidity from elsewhere in DeFi to fix the price on Aqueduct. The end result is the pool price goes back to the market rate - thus, the trader gets less price impact while the arbitrager makes a profit from fixing the price.&#x20;



The time between arbitrage swaps will vary in real world implementation and is completely dependent on the total amount of the user's swap and the time period in which they are swapping. However, in this example, we are assuming arbitrage becomes profitable every 10 seconds. The simulation tool allows you to simulate arbitrage between 1 and 60 seconds.



## Simulate the Swap

Once you change any of the three variables within the simulate swap widget, both the Aqueduct and CPAMM results will be shown. The graph displayed gives a visual representation of the price impact on each protocol.

<figure><img src="../.gitbook/assets/Screenshot 2023-05-24 at 1.52.59 AM.png" alt=""><figcaption><p>$100,000,000 Swap simulated on Aqueduct and a CPAMM</p></figcaption></figure>

### Aqueduct Results

On the bottom left widget, you should be able to see a list of variables calculated from the parameters you chose in the 'Simulate Swap' widget. We can see that the output from the trade on Aqueduct is $99,834,929.02 with a calculated price impact of 0.17% from the trader's original $100,000,000 trade. We can also see that the time taken from the trade on Aqueduct is 168 hours, or seven days. Note that the longer the trade, the less the total amount of price impact will be on Aqueduct. However, we are assuming minimal volatility in the market rate of the two assets throughout those seven days - with the actual implementation, the market rate of the two assets is likely to change.

We can also see that the total initial combined liquidity on Aqueduct was only $2,000,000. The interesting thing to point out here is that the trader was able to trade $100,000,000 with price impact of 0.17% on only $2,000,000 combined liquidity. This is made possible from arbitragers sourcing liquidity from elsewhere in DeFi throughout the life of the trade to fix the pool price on Aqueduct.

### CPAMM Results

On the bottom right widget, you should be able to see a list of variables calculated from the swap amount you initialized in the 'Simulate Swap' widget. We can see the trader's output from the trade is $50,000,000, with a calculated price impact of 50.00% from the trader's original $100,000,000 trade. We can also see that the trade was a discrete transaction as opposed to the time weighted swap on Aqueduct. Therefore, the swap took place instantly (or whenever the transaction was recorded on-chain).



We can also see that the total combined liquidity of this token pair on the CPAMM was $200,000,000. This is $198,000,000 more than the initial liquidity on Aqueduct, yet the difference in price impact between the two is substantial.



## Change the Liquidity

### Navigate to the 'Set Liquidity' Widget

At the top of the page in the nav bar, you should see an 'Add Liquidity' option, click the add liquidity button. The page displayed should look like the image below.

<figure><img src="../.gitbook/assets/Screenshot 2023-05-23 at 12.31.33 PM.png" alt=""><figcaption><p>'Set Liquidity' widget in the Aqueduct TWAMM vs CPAMM simulator</p></figcaption></figure>

### Edit the Liquidity

The first two input boxes are the pool balances for both USDC and DAI, each of which have a total of $1,000,000 in liquidity in this example. You can edit the total amount for each of these pairs here.

It's important to note that liquidity on Aqueduct can be much less than your average CPAMM and achieve better price impact for large trades than the CPAMM. For this reason, the default combined liquidity on Aqueduct is set to $2,000,000 while the default combined liquidity on the CPAMM is set to $200,000,000. Of course, the more liquidity on either AMM, the less the price impact will be for each.



### Submit the Liquidity

The liquidity given to both Aqueduct and the CPAMM will automatically be logged whenever a change is made. Navigate back to the 'Results' page to see the affect of the new liquidity ratios.



## Limitations

While this simulation tool provides good insight as to what a trade on Aqueduct will look like in comparison to a CPAMM, there are some limitations.

For one, we assume that the total liquidity available for the given tokens in the rest of DeFi is infinite. This means that you could theoretically simulate a trade worth trillions of dollars on this tool and get decent price impact depending on the liquidity set in each AMM. In reality, the total liquidity available throughout the rest of the ecosystem is unlikely to be able to support a trade of this size.

Another limitation of this tool is that we assume arbitrage is always profitable between 1 and 60 seconds. The profitability of arbitrage on Aqueduct is likely to change in relation to the size of the trade and the total amount of liquidity on the pool. This doesn't mean arbitrage will not become profitable, it just means the time in between arbitrage trades is variable. Another factor we aren't taking into account here is the gas needed for arbitragers to fix the price will also have an affect on the profitability of the arbitragers trade. Thus, the time between arbitrage trades is likely to change.
