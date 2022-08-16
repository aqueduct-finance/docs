# 🌊 Pools

Every Aqueduct pool consists of 2 Aqueduct tokens (custom super tokens). Inspired by Uniswap V2, our pools closely follow the automated market maker (AMM) pattern.

## Swaps

Our pools support a single operation: swap one token for another over a period of time. At a high level, every pool interaction will look like this:



![](<.gitbook/assets/Screenshot 2022-08-15 at 9.10.48 PM.png>)

For reference, ETHxp and USDCxp are Aqueduct pool tokens - wrapped tokens that implement additional functionality to existing erc20 tokens. Aqueduct pool tokens are also super tokens, see:

{% embed url="https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-tokens" %}

As shown, a user will start a standard (static flow rate) stream into the pool. The user will then immediately receive a custom (dynamic flow rate) return stream of the proportionate value of the opposite token. See:

{% embed url="https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-agreements/constant-flow-agreement-cfa" %}

{% embed url="https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-apps" %}

