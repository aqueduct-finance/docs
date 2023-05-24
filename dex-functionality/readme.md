---
description: How pools work on Aqueduct
---

# 🏊♀ Pools

Every Aqueduct pool represents one token pair (e.g ETH/DAI), and facilitates the exchange of each asset in both directions.

Aqueduct pools are Superfluid Super Apps. Super Apps are smart contracts that are registered with the Superfluid Protocol that are allowed "react" to Super Agreements (i.e. streams and other money primitives). A Super App "reacts" to the creating, updating, and deleting of Super Agreements, and can then run arbitrary logic as a result.

It's important to recognize that the Super App reacts atomically, meaning the arbitrary code runs within the same transaction that creates/updates/deletes the stream.

{% embed url="https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/super-apps" %}

{% hint style="info" %}
All reactions from the pool are entirely on-chain and atomic
{% endhint %}

