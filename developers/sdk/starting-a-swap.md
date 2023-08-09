# 🌊 Starting a swap

To start a position, you just need to send a stream to the desired Aqueduct pair contract. Each pair is a [super app](https://docs.superfluid.finance/superfluid/developers/super-apps) registered in the Superfluid protocol, meaning it will automatically respond to incoming streams.&#x20;



### Getting a pair's address

Aqueduct's factory contract stores pairs just like Uniswap V2's factory. You can find a pair by calling getPair on the factory contract:

```solidity
function getPair(address tokenA, address tokenB) external view returns (address pair);
```

If getPair returns the zero address, then that pair has not been created yet.



### Starting a stream

Using superfluid's js sdk, we can easily create a stream into the Aqueduct pair, which will start your swap.

<pre class="language-javascript"><code class="lang-javascript"><strong>import { Framework } from "@superfluid-finance/sdk-core";
</strong>import { ethers } from "ethers";

// init superfluid sdk
const provider = new ethers.providers.InfuraProvider(
  "matic",
  "&#x3C;INFURA_API_KEY>"
);
const sf = await Framework.create({
  chainId: 137,
  provider
});

// get addresses
const pairAddress = "...";
const daix = await sf.loadSuperToken("DAIx");

// send the stream
const signer = sf.createSigner({ privateKey: "&#x3C;TEST_ACCOUNT_PRIVATE_KEY>", provider });
const createFlowOperation = daix.createFlow({
  sender: "0x...",
  receiver: pairAddress,
  flowRate: "1000000000"
});
const txnResponse = await createFlowOperation.exec(signer);
const txnReceipt = await txnResponse.wait();
</code></pre>

If you already have a stream going to the pair, then you need to call updateFlow instead of createFlow:

```javascript
const updateFlowOperation = daix.updateFlow({
  sender: "0x...",
  receiver: pairAddress,
  flowRate: "1000000000"
});
const txnResponse = await updateFlowOperation.exec(signer);
const txnReceipt = await txnResponse.wait();
```

And to delete your stream and end your swap, call deleteFlow:

```javascript
const deleteFlowOperation = daix.deleteFlow({
  sender: "0x...",
  receiver: pairAddress
});
const txnResponse = await deleteFlowOperation.exec(signer);
const txnReceipt = await txnResponse.wait();
```

Read more:

{% embed url="https://docs.superfluid.finance/superfluid/developers/constant-flow-agreement-cfa/cfa-operations" %}

Swapped funds are held in the pair contract until they are retrieved. When your stream is updated or deleted, those funds will automatically be transferred to your address.
