---
description: What are money streams?
---

# ☄ Money streams

A money stream is a flow of money that moves every second, at a specified flow-rate between accounts with no capital lock up. For example, Alice starts a stream of 10 DAI per second to Bob. Alice’s balance will decrease every second by 10 DAI, and Bobs balance will increase by 10 DAI every second.&#x20;

To get a more in depth understanding of how streams work, we recommend you checkout the [Superfluid documentation](https://docs.superfluid.finance/superfluid/protocol-overview/what-is-superfluid). Money streams were created by the Superfluid protocol and offer a real-time solution to the current way money works. Here's a good visualization of how streams work on Superfluid:

{% embed url="https://twitter.com/Superfluid_HQ/status/1650823271535857664?s=20" %}
Super tokens going brrr...
{% endembed %}

Aqueduct uses money streaming to create a gas efficient TWAMM with less information leakage. Per-second swaps are curated by money streams with super tokens.
