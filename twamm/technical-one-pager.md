# ⚙ Technical One-Pager

Please reference Paradigm's 'TWAMM' paper:

{% embed url="https://www.paradigm.xyz/2021/07/twamm" %}

{% hint style="info" %}
The fundamental idea of the TWAMM is an AMM that supports time-based / non-atomic trades, which can also dynamically compute its reserves based on the cumulative effect of all trades in a gas-efficient manner.
{% endhint %}

### How the TWAMM computes reserves

Let's say $$x_{rate}$$ and $$y_{rate}$$ are the per-second cumulative trading rates of all combined positions, for each token respectively (e.g. if there was a single position trading 100 token x over 10 seconds, then $$x_{rate} = 10/s$$ ).

After some time $$t$$ since the last state change, we can compute $$x_{in} = t \cdot x_{rate}$$ and $$y_{in} = t \cdot y_{rate}$$.

Then, we can compute each reserve as:

$$
x_{ammEnd} = \sqrt{\frac{kx_{in}}{y_{in}}} \cdot \frac{e^{2\sqrt{\frac{x_{in}y_{in}}{k}}} + c}{e^{2\sqrt{\frac{x_{in}y_{in}}{k}}} - c}
$$

$$
y_{ammEnd}=\frac{x_{ammStart}y_{ammStart}}{x_{ammEnd}}
$$

where

$$
c=\frac{\sqrt{x_{ammStart}y_{in}} - \sqrt{y_{ammStart}x_{in}}}{\sqrt{x_{ammStart}y_{in}} + \sqrt{y_{ammStart}x_{in}}}
$$



### Efficient Computation on Paradigm's TWAMM

Trades on this model are created in a single transaction at the start of the position, with an amount and a timeframe. This means that a state change is performed at the start of the position, but not at the end.

This TWAMM uses _lazy evaluation_, meaning it computes the virtual reserves only when needed in an operation (e.g. a swap operation needs to compute the virtual reserves correctly in order to check that $$k$$ is constant).

Because $$x_{rate}$$ and $$y_{rate}$$ will change without an on-chain state change, the reserves cannot be evaluated with a closed-form expression, and instead the computational complexity will scale linearly in proportion to the number of 'virtual' changes in $$x_{rate}$$ and $$y_{rate}$$ that occur before the reserves are evaluated and updated on-chain. In order to reduce complexity, implementations can "limit the number of blocks eligible for order expiry: for example, the TWAMM could specify that orders are only eligible to expire every 250 blocks, or roughly once per hour" (paradigm).&#x20;

This figure from Cron Finance displays gas usage in relation to period of inactivity, based on different _order block intervals_:

<figure><img src="https://2434097700-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FJ7bY0xe83NKFmbUiEyBZ%2Fuploads%2FXig2W4lhpF4z2vaeC4ff%2Fimage.png?alt=media&#x26;token=f000b866-4210-47f9-9984-9c3fba85e57b" alt=""><figcaption><p>ref: <a href="https://docs.cronfi.com/twamm/fundamentals/inactivity">https://docs.cronfi.com/twamm/fundamentals/inactivity</a></p></figcaption></figure>

The clear drawback is that users may incur large, unexpected gas costs based on the pool conditions. In extreme cases, the gas cost of reserve evaluation may exceed the gas allocation for an entire block. Another issue with this model is _information leakage_: the user's deposit and timeframe are visible on-chain.&#x20;



### (More) Efficient Computation on Aqueduct's TWAMM

Trades on Aqueduct are defined by two separate transactions. The user will create a transaction at the start of the position using a [stream](../superfluid-concepts/money-streams.md), with only the per-second rate of exchange (i.e. $$x_{rate,user}$$). At some time later, the user will end their position with a separate transaction.

This model still uses lazy evaluation, but because $$x_{rate}$$ and $$y_{rate}$$ are always constant between state changes, the pool can always evaluate the reserves in constant computational complexity.&#x20;

#### Benefits:

#### ⛽  Gas - users are guaranteed a fixed gas cost, regardless of pool conditions

ℹ️  **Less information leakage - users only specify a per-second rate of trade, but there is no way to determine total amount or timeframe before their position is ended**



**Drawbacks:**

🏦  **Stream buffer - users must lock 4 hours worth of their stream on Superfluid protocol**

{% embed url="https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-agreements/constant-flow-agreement-cfa#buffer" %}
