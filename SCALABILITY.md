## References 
- https://blog.polygon.technology/the-data-availability-problem-6b74b619ffcc/
- https://docs.polygon.technology/docs/home/architecture/polygon-architecture/
- https://medium.com/offchainlabs/whats-up-with-rollup-db8cd93b314e
- https://medium.com/omgpool/plasma-vs-optimistic-rollups-9808c2f64975
- https://vitalik.ca/general/2021/01/05/rollup.html

## Plasma

### Minimum Viable Plasma
- Minimum Viable Plasma (MVP) is a design for extremely simple UTXO based chains
- MVP specification enables high-throughput payment transactions, 
- MVP does not support more complicated constructions like scripts or smart contracts.
- MVP relies on confirmation signatures
- Users need to sign a signature before making a transaction, 
- Users need to wait to see the transaction included in a valid block, and then sign another signature. 
- These second signatures must also be included within a plasma block, reducing block space available for more transactions
- Transactions are batched into single submission on the ETH chain.
- Offering finality and security for payments upto 65,000 UTXO L2 transactions

### More Viable Plasma
- Removed the need for confirmation signatures
- Considered secure as it is a child chain approach

### Polygon 
- Polygon is an adaptatio of minimum viable plasma with root chains and child chains
- Developers can use Plasma in Polygon for specific state transitions written on Plasma predicates
- Plasma predicates can be written for tokens like ERC 20, ERC 721, asset wraps and custom predicates
- Polygon has a generic validation Layer coupled with execution environments
- Polygon has a three tier architecture consisting of :
- Staking and Plasma Smart Contracts on Ethereum
- Heimdall Proof of Stake Layer
- Bor is the Block Producer Layer
- Heimdall layer handles the aggregation of blocks produced by Bor into a merkle tree 
- Heimdall also publishes the merkle root periodically to the root chain. 
- Polygon has Fraud Proofs and Exit Queues in the Root Chain
- Heimdall is the PoS validator node that works in consonance with the Staking contracts on Ethereum. 
- It is implemented by building on top of the Tendermint consensus engine
- Tendermint is adapted with changes to the signature scheme and various data structures. 
- It is responsible for block validation, block producer committee selection, checkpointing 
- For every few blocks on Bor, there is a validator on the Heimdall layer):
- Bor Validates all the blocks since the last checkpoint
- Bor Creates a merkle tree of the block hashes
- Bor Publishes the merkle root to the main chain
- Incentivised validators are running Heimdall and Bor nodes

## Sidechains
- Some of the plasma implementations are considered side chain approaches while others are considered as child chains
- Side chains are attached to Ethereum using one or two way transfer of assets
- Each side chain is self contained
- It is required to transfer the custody of tokens from parent chains to side chains

## Rollups
- In rollup, calls to the contract and their arguments are written on-chain as calldata, 
- However the actual computation and storage of the contract are done off-chain.
- Since contract execution and storage are moved off-chain, on-chain gas costs are drastically reduced.
- There are three basic approaches: 
- noninteractive rollup (like ZK-Rollup), 
- one-round interactive rollup (like the “Optimistic rollup” proposal)
- multi-round interactive rollup (like Arbitrum Rollup).

### zkRollups
- Noninteractive rollup relies on succinct validity proofs. 
- Every assertion is accompanied by an efficiently checkable proof (like a SNARK) 
- This is great for the miners and other observers, 
- The proofs are cheap to check and they establish correctness of the assertion immediately.
- Creating the proofs is incredibly expensive, unless the transactions being asserted are very simple. 
- Thus ZK-Rollup is a great approach for payment transactions

### Optimistic Rollups
- When the assertion is posted on-chain, the asserter posts a bond 
- There is a time window in which validators can challenge the assertion 
- if they think it’s wrong. this is sometimes called a “fraud proof”. If the asserter is wrong, they will lose their bond.
- An on-chain contract emulates that one challenged call and checks whether the asserter’s claim about that call was wrong. 
- If the challenge period expires with no successful challenges, the assertion is accepted and becomes final.

### Arbitrum Rollups
- Arbitrum has full smart contract support and ships with a Solidity compiler
- In multi-round interactive rollup, like  Arbitrum Rollup, there is a challenge window 
- In this window, a challenger can post a bond and claim that the assertion was wrong. 
- What follows is a back-and-forth interactive protocol between the asserter and the challenger,
- The on-chain smart contract acts as a referee for the protocol.
- In the end the referee determines that one party made a false claim, and punishes that party by taking their bond.

### Review on Optimisitc Rollups
- The choice between one-round and multi-round rollup boils down to a tradeoff between on-chain cost and time to resolve a dispute.

## Channels

## New Approach
- Oracles for data ingestion
- distributed hash table for data linking
- zkRollups for data compression
- Optimistic Rollups for data verification
- Plasma for data verification
- ETH2 as data availability layer
