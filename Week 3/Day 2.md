# Day 2: The EVM's Data Landscape: Storage, Memory, and Stack

## Day Topic & Subtopics

**Data Persistence and Cost: Where Does the Data Live?**

1. Storage: The Persistent State Machine
2. Memory: The Volatile Scratchpad
3. Stack: The Execution Register
4. Calldata: The Read-Only Input

### Lecture Notes

### 1. Storage: The Persistent State Machine

**Storage** is the most critical and expensive data location in the EVM.

- **Persistence:** Data stored here is permanent, forming the contract’s persistent internal state (e.g., user token balances, ownership records). This data is maintained across transaction executions and is recorded in the blockchain’s world state tree.
- **Structure:** It is conceptually a massive, sparse key-value map, mapping 32-byte slots to 32-byte values.
- **Cost:** Operations that write to storage (`SSTORE` opcode) are exponentially more expensive than any other operation. For instance, changing a storage location from zero to a value costs roughly 20,000 gas, while changing an existing non-zero value costs about 5,000 gas. This high cost is necessary because every node in the world must save this data permanently.

### 2. Memory: The Volatile Scratchpad

**Memory** serves as temporary, volatile storage during function execution.

- **Persistence:** It is wiped clean after each external function call or message call finishes executing.
- **Structure:** It is a linear, byte-addressable array.
- **Cost:** Memory operations (like `MSTORE` or `MLOAD`) are relatively cheap compared to storage, costing only around 3 gas per word (32 bytes). It acts like a temporary notepad used for complex calculations and data manipulation.

### 3. Stack: The Execution Register

The **Stack** is used exclusively for immediate computation.

- **Persistence:** Highly volatile; only exists during opcode execution.
- **Access:** It supports LIFO operations, meaning you can only access the topmost elements. To reach deeper elements, you must remove the ones on top first.
- **Cost:** Gas costs are similar to memory, but the compiler manages the overhead of shuffling elements.

### 4. Calldata: The Read-Only Input

**Calldata** is a special, immutable area used exclusively for storing function arguments (parameters) passed during an external function call. It is non-modifiable, highly efficient for large inputs, and its contents are transient, existing only for the duration of the external call.

| Data Location | Persistence | Purpose | Relative Cost | Access |
| --- | --- | --- | --- | --- |
| **Storage** | **Permanent** (Stored on blockchain) | Contract's long-term state (balances, records) | **Extremely High** (20,000+ gas to write) | Key-value map |
| **Memory** | **Volatile** (Wiped after call) | Temporary data for computation/arrays | **Low** (3 gas per word) | Linear array |
| **Stack** | **Volatile** (Wiped after opcode) | Immediate instruction inputs/outputs | **Very Low** | LIFO (Last-In, First-Out) |
| **Calldata** | **Volatile** (Exists only during external call) | Read-only input arguments | **Very Low** (External function arguments) | Read-only |

Export to Sheets

### Visual Aids & Analogies

### Analogy: Filing Cabinets vs. Whiteboard

- **Storage (Filing Cabinets):** This is where you keep the original, legal deeds, records, and balances. It is permanent, meticulously organized, and very expensive to update, requiring formal procedures (`SSTORE`) that must be logged by the whole network.
- **Memory (Whiteboard):** This is the temporary whiteboard used during a meeting. You write down calculations, draft proposals, and temporary arrays. It's cheap to write on, but once the meeting is over (function execution ends), the whiteboard is erased.
- **Stack (Calculator Display):** This is the display register of your calculator. It holds the two numbers you are currently adding or multiplying. It’s the fastest and most temporary workspace.

### Practical Exercises

**Exercise 2.1: Analyzing Storage Cost in Remix**

1. Students create a simple contract in Remix with a state variable (`uint256 public myNumber;`).
2. They write a function to set this number (`function setNumber(uint256 _num) public { myNumber = _num; }`).
3. They use the transaction analysis feature in Remix to find the gas cost of the `setNumber` transaction and discuss how the high cost reflects the permanent storage write operation.

### Class Discussion Prompts

1. **Immutability Tax:** Why does the simple act of writing a 32-byte number to a contract's storage cost thousands of units of gas, even though the same operation on a conventional computer is nearly instant? (Hint: Relate the cost directly to the distributed nature and the network’s need to store it perpetually).
2. **Solidity Optimization:** If a function needs to define a temporary array, why should a developer explicitly use the `memory` keyword instead of allowing the compiler to potentially place the data in a more expensive location?.