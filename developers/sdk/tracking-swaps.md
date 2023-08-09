# 🔍 Tracking swaps

### Super token balances

As your stream runs, your balance will slowly decrease based on your specified flowrate. You can track your real-time balance as follows:

```javascript
import { Framework } from "@superfluid-finance/sdk-core";
import { ethers } from "ethers";

// init superfluid sdk
const provider = new ethers.providers.InfuraProvider(
  "matic",
  "<INFURA_API_KEY>"
);
const sf = await Framework.create({
  chainId: 137,
  provider
});

// get token
const daix = await sf.loadSuperToken("DAIx");

// call balanceOf
const currentBalance = await daix.balanceOf({
  account: "0x...",
  providerOrSigner: provider
});
```

Super tokens follow the erc-20 interface, so you can also simply call balanceOf on the super token's contract using a standard library like ethers or viem.



### Locked swap balances

Swapped funds are held in the pair contract until they are retrieved. To get the real-time locked amounts, call getRealTimeUserBalances on the pair contract:

```solidity
function getRealTimeUserBalances(
    address user
) public view returns (uint256 balance0, uint256 balance1, uint256 time);
```

Or, you can query the locked amounts at some future timestamp by calling getUserBalancesAtTime:

```solidity
function getUserBalancesAtTime(
    address user, 
    uint32 time
) public view returns (uint256 balance0, uint256 balance1);
```

Note that time should be greater than the block timestamp when your position was started, and that the returned balances assume there will be no new interactions with the pair before that time.



### Retrieving locked swap balances

When you update or delete your stream, your current locked funds will all be transferred to you. To manually retrieve your funds without changing your position, call retrieveFunds on the pair contract:

```solidity
function retrieveFunds(
    ISuperToken _superToken
) external returns (uint256 returnedBalance);
```
