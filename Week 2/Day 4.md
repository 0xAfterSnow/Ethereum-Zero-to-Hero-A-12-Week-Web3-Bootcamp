# Day 4: Transaction Flow and Querying the Chain

## Day Topic & Subtopics

**Putting it all Together: Querying the Live Network**

1. Transaction Lifecycle Review: From Mempool to Finality
2. EOA-to-Contract Interaction Workflow
3. Hands-on: Querying Block Data with Foundry `cast`
4. Hands-on: Monitoring Network Events with Ethers.js

### Lecture Notes

### 1. Transaction Lifecycle Review

A transaction is the formal instruction (signed by an EOA) to modify the Ethereum state.

1. **Creation & Signing:** The user creates the transaction (recipient, value, data, gas limits) and signs it using their private key (ECDSA).
2. **Broadcast & Mempool:** The signed transaction is broadcast to a node, which places it into the public Mempool.
3. **Selection:** A Validator selects the transaction (prioritizing high Priority Fees) and includes it in a new block.
4. **Execution:** The Execution Layer (EVM) processes the transaction, performs the computational steps (opcodes), updates the state temporarily, and deducts the gas fee.
5. **Validation & Consensus:** The Consensus Layer validates the block through attestations, ensuring all nodes agree on the new state.
6. **Inclusion & Finality:** The block is added to the chain, the state change is made permanent, and the transaction is considered finalized.

### 2. EOA-to-Contract Interaction

The true power of Ethereum is unlocked when an EOA interacts with a Contract Account. The user's transaction often includes a `data` payload, which specifies which function in the contract to call and the arguments to pass.

- **Read Calls (`view`/`pure`):** These do not change the state (e.g., querying a balance). They are generally free when done directly via an RPC provider (like Alchemy or Infura) and only happen locally on the querying node.
- **Write Calls (State-Changing):** These modify the contract's storage (e.g., sending tokens). These require gas payment, EOA signature, and network confirmation.

### 3. Hands-on: Querying Block Data with Foundry `cast`

Foundry’s `cast` is an indispensable command-line interface (CLI) tool for interacting directly with the blockchain. It allows developers to quickly query RPC endpoints without needing complex JavaScript code.

### Code Examples (CLI)

Bash

```jsx
# Query the latest block number on the Ethereum Sepolia Testnet
# Replace YOUR_RPC_URL with an actual Alchemy/Infura endpoint for Sepolia
export ETH_RPC_URL="YOUR_RPC_URL"
cast block-number

# Retrieve the full details (header and body) of the latest block
cast block latest --full

# Retrieve a specific field (e.g., the State Root) from the finalized block
cast block finalized --field stateRoot

# Inspect a specific, simple transaction (e.g., a simple ETH transfer)
# Note: Requires knowing a tx hash, use Etherscan to find one
# cast tx <TX_HASH>
```

### 4. Hands-on: Monitoring Network Events with Ethers.js

Ethers.js allows us to programmatically read state from a blockchain provider.

### Code Examples (Ethers.js Read-Only)

JavaScript

```jsx
// Block Explorer Reader: Display details of the last 10 finalized blocks
const { ethers } = require('ethers');

// Ensure you have a provider configured
const provider = new ethers.providers.JsonRpcProvider("YOUR_RPC_URL");

async function readLastBlocks(count = 10) {
    // Get the current finalized block number
    const latestBlockNumber = await provider.getBlockNumber();
    console.log(`Current Latest Block: ${latestBlockNumber}`);

    const startBlock = latestBlockNumber - count + 1;

    for (let i = startBlock; i <= latestBlockNumber; i++) {
        // Fetch the block data
        const block = await provider.getBlock(i); 

        // Block data is a rich object; we extract key metrics
        console.log(`\nBlock #${block.number}`);
        console.log(`  Hash: ${block.hash.substring(0, 10)}...`);
        console.log(`  Timestamp: ${new Date(block.timestamp * 1000).toLocaleString()}`);
        console.log(`  Transaction Count: ${block.transactions.length}`);
        console.log(`  Total Gas Used: ${block.gasUsed.toString()}`);
    }
}

readLastBlocks(10).catch(console.error);

// Note: Reading a public state variable from a deployed contract (read-only)
/* 
// Assumes SimpleStorage contract is deployed at a known address
const contractAddress = "0x...";
const contractAbi = ["function get() view returns (uint256)"]; // Human-readable ABI fragment
const contract = new ethers.Contract(contractAddress, contractAbi, provider);

async function readState() {
    const value = await contract.get(); 
    console.log("Current stored value:", value.toString()); // Read public state
}
*/
```

### Visual Aids & Analogies

### Visual Aid: Etherscan Interface

Use a screenshot of an Etherscan transaction page to visually correlate the fields we’ve discussed **Nonce**, **Gas Used**, **Base Fee**, **Tx Data** with their real-world representation.

### Practical Exercises

**Exercise 4.1: Building a Basic Block Explorer Reader**

1. Implement and run the `readLastBlocks` Ethers.js function in a local Node.js environment.
2. Modify the function to specifically retrieve the `miner/validator` address and the `baseFeePerGas` for each block.
3. (Milestone) Compare the **Transaction Count** of the most recent 10 blocks to visually gauge the current network activity and congestion.

### Class Discussion Prompts

1. **Reading vs. Writing:** Explain the security and efficiency implications of why reading data from a contract using a `view` function off-chain is free (no gas, no signature needed), but modifying that state requires the full, signed transaction process.
2. **Scalability Crunch:** The data retrieved in the exercise (transaction count, gas usage) demonstrates Ethereum’s limited throughput (transactions per second). How do these inherent L1 constraints structurally justify the entire focus of the modern curriculum on Layer 2 (L2) scaling solutions?
