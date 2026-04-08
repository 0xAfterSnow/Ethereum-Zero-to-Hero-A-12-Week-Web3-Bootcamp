# Day 4: Hands-on EVM Interaction and Deployment Analysis

## Day Topic & Subtopics

**EVM Analysis and Gas Efficiency**

1. Solidity-to-EVM: Bytecode and Opcodes
2. Hands-on: Remix IDE Opcode Analysis
3. Ethers.js: Reading Transaction Receipts for Gas Analysis
4. Short Project: EVM State Changer

### Lecture Notes

### 1. Solidity-to-EVM: Bytecode and Opcodes

When you compile a Solidity contract, the human-readable code is translated into **EVM Bytecode** a long hexadecimal string. This bytecode is merely a sequence of opcodes and their arguments. This is the code that is deployed to the blockchain and executed by the EVM.

- **Contract Accounts:** Once deployed, the contract's bytecode is permanently associated with its Contract Account address. When a transaction is sent to this address, the EVM starts executing the bytecode.

### 2. Hands-on: Remix IDE Opcode Analysis

The Remix Integrated Development Environment (IDE) is a powerful tool for analyzing this low-level execution.

- **Debugging:** We can use Remix to deploy a simple contract to the built-in Remix VM. After executing a transaction (e.g., calling a `set` function), the debugger allows us to step through the execution, viewing the state of the Stack, Memory, Storage, and the current Opcode being processed.
- **Gas Estimation:** Remix also provides precise gas estimations for deployment and function calls, allowing instant feedback on the relative efficiency of different code implementations.

### 3. Ethers.js: Reading Transaction Receipts for Gas Analysis

To analyze the real-world cost of a deployed transaction, developers must inspect the transaction receipt provided by the network.

- **Receipt Data:** The transaction receipt contains final, deterministic data, including:
    - `gasUsed`: The exact units of gas consumed by the transaction.
    - `cumulativeGasUsed`: The total gas used in the block up to this transaction.
    - `effectiveGasPrice`: The final, actual price paid per unit of gas (Base Fee + Tip).
- **Analysis:** Multiplying `gasUsed` by `effectiveGasPrice` provides the final ETH cost of the transaction, which is critical for measuring dApp performance and user costs.

### Code Examples

We will use Ethers.js to read a transaction receipt, similar to the process used in the provided curriculum milestone.

```jsx
// Ethers.js: Analyzing a Transaction Receipt for Gas Cost
const { ethers } = require('ethers');

// 1. Setup Provider (Use a public testnet like Sepolia)
const RPC_URL = "YOUR_SEPOLIA_RPC_URL"; 
const provider = new ethers.providers.JsonRpcProvider(RPC_URL);

// NOTE: Replace with a real transaction hash from a recent Sepolia deployment
const TX_HASH_TO_ANALYZE = "0x..."; 

async function analyzeGasCost() {
    console.log(`Analyzing transaction: ${TX_HASH_TO_ANALYZE}`);
    
    // 2. Fetch the transaction receipt
    const receipt = await provider.getTransactionReceipt(TX_HASH_TO_ANALYZE);

    if (!receipt) {
        console.log("Receipt not found. Has the transaction been mined yet?");
        return;
    }
    
    // 3. Extract key data points from the receipt
    const gasUsed = receipt.gasUsed;
    
    // The effectiveGasPrice reflects the actual Base Fee + Priority Fee paid
    const effectiveGasPrice = receipt.effectiveGasPrice; 
    
    // 4. Calculate the total cost in Wei (smallest unit)
    const totalCostWei = gasUsed.mul(effectiveGasPrice);

    // 5. Convert total cost from Wei to ETH for readability
    const totalCostEth = ethers.utils.formatEther(totalCostWei);

    console.log(`\n--- Gas Analysis ---`);
    console.log(`Status: ${receipt.status === 1? 'Success' : 'Failed'}`);
    console.log(`Gas Units Used: ${gasUsed.toString()}`);
    console.log(`Effective Gas Price: ${ethers.utils.formatUnits(effectiveGasPrice, 'gwei')} Gwei`);
    console.log(`Total Transaction Cost: ${totalCostEth} ETH`);
}

// You can uncomment the function call to run it:
// analyzeGasCost().catch(console.error);
```

### Visual Aids & Analogies

### Visual Aid: Transaction Receipt Dissection

Display a clear image of a transaction receipt from a block explorer (e.g., Etherscan) and use call-outs to map the fields: `Gas Used`, `Effective Gas Price`, and `Transaction Fee` back to the theoretical EIP-1559 formula.

### Practical Exercises

Short Project 3.1: EVM State Changer 

1. **Deployment:** Deploy a minimal contract on the Sepolia Testnet (using Hardhat/Foundry or Remix) that updates a single storage variable (e.g., a simple counter).
2. **Execution:** Call the function to update the storage variable.
3. **Analysis:** Retrieve the transaction receipt using the Ethers.js script above.
4. **Report:** Generate a report detailing the precise `gasUsed` for the storage write operation and the resulting ETH cost, fulfilling the week's hands-on milestone requirement.

### Class Discussion Prompts

1. **Out-of-Gas Strategy:** If a developer realizes their transaction is failing due to an "Out-of-Gas" error, what are the two main ways they can fix this problem? (Hint: One is user-side, one is developer-side).
2. **Code Optimization:** Based on the high cost of `SSTORE`, name two Solidity best practices a developer should follow to minimize gas costs in their contracts. (Hint: Think about state variables and logging).