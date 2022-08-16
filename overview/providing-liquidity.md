# 🚰 Providing Liquidity

A liquidity provider (LP) will stream in a proportionate amount of both token A and token B, so as to maintain the previous ratio of liquidity:

![](<../.gitbook/assets/Screenshot 2022-08-15 at 10.12.35 PM.png>)

As shown, the LP receives proportionate streams of each token. Until another user interacts with the pool, the LP's balance of each token will remain unchanged. For the first time ever, users can earn yield while still retaining control over their assets.



## What happens after the next swap?

For the purpose of demonstration, let's say that the LP is providing the initial liquidity to the pool. After the next user makes a swap, both of the LP's outgoing streams will be updated:

![](<../.gitbook/assets/Screenshot 2022-08-15 at 10.36.46 PM.png>)

It is important that our pools do not retain funds. As shown above, all funds are perfectly redistributed.&#x20;
