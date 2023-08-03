# AqueductV1Factory

The factory contract remains mostly unmodified from Uniswap V2's [factory](https://docs.uniswap.org/contracts/v2/reference/smart-contracts/factory) contract.&#x20;



## What stays the same

* The factory controls the `feeTo` address
  * By default, `feeTo` is set to the zero address. When changed to another address, this represents the activation of the 'fee switch', and 1/6 of all future minted liquidity will belong to that address
  * The factory's `setFeeToSetter` function allows us to change or delegate the permissions for the fee switch. If `feeToSetter` were set to the zero address, then the fee switch would be permanently frozen in its current state
* The factory handles creation of pairs and storage of pair addresses
  * Only one pool can be created per token pair



## What changed

* The factory now deploys an auction contract in the constructor and stores its address
  * because the auction contract is a core part of the protocol, this address is immutable and permanently tied to the factory and all of its pairs
* Each pair is built on Superfluid protocol as a '[super app](https://docs.superfluid.finance/superfluid/developers/super-apps)', meaning it contains hooks that atomically respond to stream creation, updates, and deletion
  * To enable this, the `createPair()` function is modified to register each new pair as a super app on Superfluid protocol's [host](https://docs.superfluid.finance/superfluid/protocol-overview/in-depth-overview/superfluid-host) contract
