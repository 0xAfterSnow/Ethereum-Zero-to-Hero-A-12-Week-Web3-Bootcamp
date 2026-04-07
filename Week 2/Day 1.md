# Day 1: The Ethereum World Computer and Layered Architecture

**Day Topic & Subtopics**

**The Distributed Engine: EVM, State, and Dual Layers**

1. Ethereum as a Transaction-Based State Machine (The World Computer)
2. The Two Critical Layers: Execution (EL) vs. Consensus (CL)
3. Ethereum State vs. Storage: A Deep Dive into Persistence
4. Types of Accounts: EOA vs. Contract Accounts

### Lecture Notes

### 1. Ethereum: The World Computer Analogy

Ethereum is frequently described as a **"World Computer"**. This analogy is apt because, like a single global machine, it runs code (smart contracts) exactly as programmed, providing a highly consistent, deterministic execution environment that is resistant to censorship or downtime.

Technically, Ethereum is a **Transaction-Based State Machine**. It starts from a "Genesis State" (Block 0). Each time a valid transaction is executed, the network transitions from the "Current State" (the complete, agreed-upon record of all accounts, balances, and contract storage) to a "New State". All nodes must agree on the final resulting state for the transaction to be considered valid and included in the canonical chain.

### 2. The Two Critical Layers (Post-Merge)

Since the transition from Proof-of-Work (PoW) to Proof-of-Stake (PoS)—known as The Merge—Ethereum operates using a dual-client architecture, separating its primary responsibilities into two distinct, communicating layers:

- **The Execution Layer (EL):** This layer (formerly "Eth1") is responsible for transaction processing and the running of the Ethereum Virtual Machine (EVM).
    - **Function:** It receives transactions, executes the smart contract code (opcodes), calculates gas consumption, and manages the network's state (account balances, contract code, and storage).
    - **Client Software:** Clients like Geth, Nethermind, and Reth handle the EL functions.
- **The Consensus Layer (CL):** This layer (formerly the "Beacon Chain") is responsible for maintaining the security and agreement of the network.
    - **Function:** It enforces the Proof-of-Stake protocol, manages the registry of validators, schedules block proposals, and, crucially, ensures that all nodes agree on the canonical order and state of the chain. It confirms blocks through **attestations** and applies **finality**, meaning the block can no longer be modified.
    - **Client Software:** Clients like Prysm, Lighthouse, and Teku handle the CL functions.

The two layers communicate seamlessly via a standardized interface called the Engine API. This separation allowed Ethereum to upgrade its consensus mechanism without affecting the execution layer (where all transaction history and smart contract data reside).

### 3. State vs. Storage

Developers often confuse "State" and "Storage."

- **Ethereum Global State (World State):** This is the single, instantaneous snapshot of all information on Ethereum. It is a massive, highly efficient database that maps every single account address to its associated account information (balance, nonce, code, and storage hash). The global state is not stored directly inside blocks; rather, the block header contains a cryptographic fingerprint (**State Root**) of the state *after* the block's transactions are executed.
- **Contract Storage (Internal State):** This is the persistent, database-like memory specific to a single smart contract. It is a permanent map of 32-byte slots to 32-byte values where a contract stores its data (e.g., user balances, ownership records). Writing to storage is the most computationally expensive operation in the EVM, as it changes the global state and must be perpetually maintained by all nodes.

### 4. Account Types

Ethereum has two fundamental types of accounts:

- **Externally Owned Accounts (EOAs):** Controlled by a private key held by an external entity (the user). They can initiate transactions but cannot contain code or execute complex logic.
    - *Analogy:* A person with a wallet.
- **Contract Accounts (CAs):** Controlled by the code permanently stored at their address. They cannot initiate transactions themselves but execute their logic automatically when called by an EOA or another contract.
    - *Analogy:* A vending machine; it holds funds and responds to valid input, but cannot spontaneously "wake up" and act.

### Visual Aids & Analogies

### Analogy: The City Hall (Ethereum State)

Imagine Ethereum's **Global State** as the official records held in a City Hall. Every resident's file (account address) is stored, including their current bank balance, property deeds (NFTs), and any active contract rules (smart contract code). When a transaction occurs (e.g., buying property), the city records are updated, and a new, verified snapshot (the State Root) is published.

### Analogy: The Assembly Line (Execution and Consensus)

The Ethereum network can be viewed as a large, continuous factory.

- **Execution Layer (EL):** The **Assembly Line** that performs the actual *work*. It takes raw inputs (transactions) and runs the code (EVM), producing a product (the updated state of the world).
- **Consensus Layer (CL):** The **Quality Control Manager**. It stands over the assembly line, ensuring every block produced follows the rules (PoS), checks the product (updated state) for defects, and certifies that the entire factory agrees on the final, canonical output.

### Practical Exercises

**Exercise 1.1: Tracing the State Root**

1. Students should search for a recent, finalized block on a block explorer (e.g., Etherscan).
2. Locate the **State Root** (often labeled as `stateRoot` or `postState`) in the block header.
3. Discuss why this single, small hash value (the root of the Merkle Patricia Trie) is sufficient to cryptographically verify the integrity of the *entire* state of Ethereum, containing billions of data points.

### Class Discussion Prompts

1. **Immutability vs. Upgrades:** How does the separation of the Execution Layer (maintaining historical data) and the Consensus Layer (managing the PoS protocol) demonstrate Ethereum's ability to undergo fundamental protocol changes (like The Merge) while keeping its entire transaction history intact?
2. **Centralization Risk:** Running a full or archive node requires significant hardware and storage. How does the high operational cost of maintaining the Global State potentially undermine the philosophical goal of decentralization, and what steps (like the invention of Light Nodes) aim to mitigate this?
