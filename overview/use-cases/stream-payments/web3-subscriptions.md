# 💳 Web3 Subscriptions

Let's say you operate a music streaming platform and want to start accepting web3 subscriptions.

One option is an approval based model. This creates a poor UX because users have to manually permission their token spending limit, and also manually pay the provider every month.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-19 at 12.02.29 AM (1).png" alt=""><figcaption></figcaption></figure>

On-chain streams on Superfluid protocol enable users to pay for a subscription simply by creating a stream with a single transaction, which pays the provider a little bit every second. This model also represents the perfect exchange of goods and services, enabling the user to cancel whenever they want.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-19 at 12.02.39 AM.png" alt=""><figcaption></figcaption></figure>

This model is great, but as a provider, you need to be paid in USDC. One option you have is to force users to pay with streams of USDCx, and leave it up to them to convert whatever tokens they have in their wallet into USDCx. This is obviously a poor UX, and will likely limit your user base.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-19 at 12.02.51 AM (1).png" alt=""><figcaption></figcaption></figure>

Ok, you don't want to limit my potential user base, so let's start accepting various tokens. In the example below, you start receiving separate streams of DAIx, ETHx, and EUROCx. The problem here is that you need USDC to pay your developers, hosting services, etc. Whenever you need USDC, you now have to incrementally convert every single one of these tokens separately on an exchange like Uniswap, which costs you time and money, and scales with how often you need liquidity in USDC. As the real-time economy grows, most services will need to pay contributors and infrastructure providers every second, which would require immediate liquidity. Under this model, this would become increasingly difficult to manage.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-19 at 12.03.15 AM.png" alt=""><figcaption></figcaption></figure>

Let's solve this problem by swapping each of these tokens to USDC every second, with Aqueduct. Under this model, we now have a perfectly automated system for web3 subscriptions, end to end. Your users are happy because they can pay for the service every second with a stream, in any token of their choosing. You are happy because you get paid every second in USDC.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-19 at 12.03.27 AM (1).png" alt=""><figcaption></figcaption></figure>
