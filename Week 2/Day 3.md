# Day 3: Gas, EVM Execution, and Runtime Components
## Day Topic & Subtopics

**The Execution Environment: EVM and Computation Cost**

1. The EVM as a Stack Machine
2. EVM Runtime Components: Stack, Memory, Storage
3. The Gas Mechanism: Purpose, Units, and Cost
4. Analyzing Opcode Execution

### Lecture Notes

### 1. The EVM as a Stack Machine

The **Ethereum Virtual Machine (EVM)** is the runtime environment that executes all smart contract code. It is critical because it ensures deterministic execution: given the same starting state and transaction, every single node running the EVM will produce the exact same resulting state.

The EVM is modeled as a **Stack-Based Machine**.

- **Stack:** A list of 32-byte items used to hold the inputs and temporary outputs of smart contract instructions. Operations (called **Opcodes**) like `ADD`, `PUSH`, or `POP` manipulate the data stored here.
- **Determinism:** The stack architecture is fundamental to determinism, as it forces a strict, predictable order of operations, eliminating the possibility of race conditions or inconsistent results across different nodes.

### 2. EVM Runtime Components

Beyond the Stack, the EVM manages three key memory/storage types:

| Component | Characteristics | Purpose | Persistence |
| --- | --- | --- | --- |
| **Stack** | Fast, temporary, limited size (1024 items max) | Inputs and outputs for computation (Opcodes) | Volatile (exists only during execution) |
| **Memory** | Linear, byte-addressable array, volatile | Temporary data storage for complex function arguments, internal arrays | Volatile (exists only during execution) |
| **Storage** | Permanent, persistent map (2^256 slots) | Stores the contract's long-term state data (e.g., account balances) | Persistent (saved to the blockchain's state tree) |

Export to Sheets

### 3. The Gas Mechanism

Gas is the measure of the computational effort required to execute an operation on the EVM.

- **Purpose:** Gas is an abstraction of processing power and time. It serves two main functions:
    1. **Preventing Abuse:** It prevents malicious actors from running infinite loops or computationally intensive operations, which would stall the network.
    2. **Incentivization:** It compensates the Validators (formerly miners) for the computational resources they expend to execute and verify transactions.
- **Calculation:** The total transaction fee (paid in ETH) is calculated as:
    
    Gas Fee=Units of Gas Used×(Base Fee+Priority Fee)
    
- **Gas vs. Gwei:** **Gas Units** measure the computational work, while **Gwei** (1 billionth of 1 ETH) is the denomination used to price each unit of gas.

### 4. Analyzing Opcode Execution

Every action in the EVM is broken down into low-level instructions called **Opcodes** (e.g., `SLOAD`, `SSTORE`, `ADD`). Each opcode has a predetermined, fixed gas cost.

- **Gas Costs:** Reading from storage (`SLOAD`) is significantly cheaper than writing to storage (`SSTORE`), as reading is a local lookup, while writing changes the Global State and must be broadcast and permanently stored by all nodes. This difference compels developers to design highly efficient storage patterns in their smart contracts.

### Code Examples

We will simulate a simple gas cost analysis using the Remix IDE (or conceptually).

```solidity
// Example: Demonstrating Gas Cost Intuition in Solidity
// (This is conceptual code meant for EVM analysis, not deployment)

pragma solidity ^0.8.0;

contract GasEconomy {
    // 1. A State Variable (Stored permanently in Storage)
    uint256 public storedNumber = 10; 

    // Cost: Very high, due to SLOAD (read) and SSTORE (write) opcodes.
    function updateNumber(uint256 _newNumber) public {
        storedNumber = _newNumber; 
    }
    
    // 2. A Pure Function (No access to State/Storage)
    // Cost: Very low, runs locally, only stack and memory opcodes used.
    function calculateSum(uint256 a, uint256 b) public pure returns (uint256) {
        return a + b; // Uses ADD opcode, low gas cost.
    }

    // 3. A View Function (Reads from Storage)
    // Cost: Low to Moderate. Uses SLOAD opcode. Transaction is typically free 
    // when called off-chain (via an RPC call), but still uses gas when called 
    // internally by another contract.
    function getNumber() public view returns (uint256) {
        return storedNumber; 
    }
}
```

### Visual Aids & Analogies

### Analogy: The City Planner (Gas)

Gas is like the computational budget assigned to an action.

- If you build a small shed (simple transaction), you need very little budget (gas).
- If you build a skyscraper (complex smart contract interaction), you need a massive budget.
- If your budget runs out before the skyscraper is finished (**Out-of-Gas Error**), all the work done is instantly demolished, and you still pay the city fees for the time the construction crew worked.

### Visual Aid: Stack Operation

![Untitled-2025-10-09-16107.png](attachment:f88c3027-37b6-44ed-8a0b-7c79b906404e:Untitled-2025-10-09-16107.png)

### Practical Exercises

**Exercise 3.1: Gas Cost Intuition**

1. Use the Remix IDE or an online EVM Opcode tool to analyze the Solidity `updateNumber` function from the Code Examples.
2. Identify which high-cost opcodes (`SSTORE`) are involved in writing to persistent storage.
3. Design a scenario where a loop in a smart contract runs too many times, forcing an **Out-of-Gas Error**, and observe how the network handles this failure (all state changes are reverted, but the sender pays the consumed gas).

### Class Discussion Prompts

1. **User Adoption Barrier:** The mandatory, preemptive payment of gas fees represents a major hurdle for mainstream user adoption. Discuss how the need for gas structurally validates the importance of future concepts like Account Abstraction (ERC-4337), which aims to decouple asset control from the single key.
2. **Efficiency and Cost:** Why must developers be obsessively focused on optimizing their code to avoid unnecessary `SSTORE` operations? How does gas cost directly translate into the viability and competitiveness of a decentralized application (dApp)?
