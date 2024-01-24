# Token Bridges

We have two bridges as explained below

1. XCapital Bridge:  ****The bridge, based on POA's bridge implementation, is used to transfer XCapital tokens between the XCapital chain and the Ethereum network.
2. XCBC20 token bridge: This bridge is used to transfer XCBC20 tokens into XCapital chain and back. Please not that XCapital bridge is not supposed to be used to transfer  . 

The bridge, based on POA's bridge implementation, is used to transfer XCapital tokens between the XCapital chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network \(whether it's XCapital or Ethereum\) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender.

The validators of the bridge on both network are the XCapital chain validators. This means that validators, as part of their governance responsibilities, also need to validate bridge transactions and therefore hold XCapital tokens to "approve" bridge transactions on XCapital chain and hold ETH to "approve" transactions on Ethereum.

Each bridge transaction must be approved by a majority \(over 50%\) of the validators in order to be processed successfully.

The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of XCapital tokens between the two networks, the bridge is also responsible for network core functionality events:

**Mint block reward distributed on the XCapital chain on Ethereum**

Each cycle the total block reward distributed on XCapital chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on XCapital chain, waiting for all bridge validators on XCapital chain to sign it, and eventually sending a transaction to mint on Ethereum \(by the last signing validator\).

**Update XCapital chain validators on Ethereum**

Each cycle the XCapital chain validators are selected from a random snapshot of pending validators.

Those validators, being also the bridge validators, need to be updated on Ethereum as well.

This works by listening to the \`InitiateChange\` event emitted by the Consensus contract on XCapital chain, waiting for all bridge validators on XCapital chain to sign it, and eventually sending a transaction to set the bridge validators on Ethereum \(by the last signing validator\).

{% hint style="info" %}
XCapital chain bridge - [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://xcscan.com/address/0xd617774b9708f79187dc7f03d3bdce0a623f6988)

Ethereum bridge - [0x5f5A17f45f64717300527236eD1B50054eAdB76E](https://etherscan.io/address/0x5f5A17f45f64717300527236eD1B50054eAdB76E)

XCapital token on Ethereum - [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d)
{% endhint %}

**Using the bridge**

**Transfering from Ethereum mainnet to Fusenet** - Send your erc20 XCapital tokens to the Ethereum bridge for them to be released from the XCapital chain bridge and be avaliable in your native XCapital wallet.

**Transfering from Fusenet to Ethereum mainnet** - Send your Native XCapital tokens to the XCapital chain bridge for them to be released from the mainnet bridge and be avaliable in your Mainnet wallet. 

