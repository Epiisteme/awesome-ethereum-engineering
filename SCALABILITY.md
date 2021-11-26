## Base Layer
- Based on scaling how much data blocks can hold
- Not based on efficiency of on-chain computation or IO operations. 
- EIP 2929 to ensure that the chain is safe against DoS attacks at current gas levels
- EIP 1559 for ETH burn and to make it easy to send transactions
- New elliptic curve precompiles, quite significant for zkRollups

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

### Optimistic Rollups

### Arbitrum
- Arbitrum has full smart contract support and ships with a Solidity compiler

## Channels

### New Approach
- Oracles for data ingestion
- distributed hash table for data linking
- zkRollups for data compression
- Optimistic Rollups for data verification
- Plasma for data verification
- ETH2 as data availability layer
