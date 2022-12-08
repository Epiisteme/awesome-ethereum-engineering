- Advanced Calldata Compression
- Separate execution of Common transactions and fault proofs
- Sequencing of transactions, batch and compress and commit to L1
- Sequencing of transactions, generation of state transition function, L2 block production, L1 settlement
- Combination of sequencer and state transition function keeps the fees low by rejecting invalid transactions
- Nodes get the sequences through real time feed and batches posted on L1
- Sequencer batches are compressed through an algorithm known as brotli
- Nitro environment consists of Node functions, ArbOS and Geth core in a geth sandwitch architecture
- ArbOS decompresses and parses sequencer data batches
- ArbOS supports cross chain bridge functionalities
- State Transition Function takes transaction bytes as inputs and has access to a modifiable copy of state tree
- State Transition Function execution modifies the state and emit the header of the new block which will be appended to the Nitro chain