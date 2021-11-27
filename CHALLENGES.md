
## Data Availability Problems
- Peers in the blockchain network should be able to ensure that the data of newly proposed block is available
- If the data is not available, the block might contain malicious transactions which are being hidden by the block producer. 
- Even if the block contains non-malicious transactions, hiding them might compromise the security of the system.

## Data Availability and zkRollups
- user submits a ZK-Proof on Ethereum which is verified. 
- If user does not submit all the transactional data on Ethereum, 
- The proof ensures that all state transitions taken in the rollup are valid
- Still users of the rollup might be in the dark about their current account balances. 
- The submitted proof sheds no light on the current states because of the Zero-Knowledge nature of it.
