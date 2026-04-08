# Day 1: The Ethereum Virtual Machine (EVM) Runtime

## Day Topic & Subtopics

**The Distributed Engine: EVM and Determinism**

1. The EVM's Role as a Stack-Based Machine
2. EVM Core Components: Program Counter and Opcodes
3. Determinism: The Requirement for Universal Agreement
4. EVM Runtime Life Cycle

### Lecture Notes

### 1. The EVM as a Stack-Based Machine

The Ethereum Virtual Machine (EVM) is not a physical computer but a secure, isolated runtime environment that exists on every single node on the Ethereum network. Its fundamental purpose is to execute smart contract code consistently and reliably across all distributed nodes.

The EVM utilizes a **Stack-Based Architecture**:

- **Stack:** A simple, Last-In, First-Out (LIFO) data structure. This is the EVM's primary workspace for holding the 32-byte inputs and temporary results of computational instructions. Operations like `PUSH`, `POP`, and `ADD` manipulate the stack directly.
- **Word Size:** All data elements processed by the EVM are standardized to 256 bits (32 bytes). This size is chosen to facilitate native cryptographic operations, such as hashing and elliptic curve math, which require 256-bit operands.

### 2. EVM Core Components and Opcodes

The EVM executes bytecode sequentially, one low-level instruction, or **Opcode**, at a time.

- **Opcode:** Each opcode (e.g., `ADD`, `JUMP`, `SSTORE`) represents a specific operation and has a predetermined, fixed gas cost. This set of instructions is the DNA of smart contracts.
- **Program Counter (PC):** A pointer that tracks the address of the next opcode instruction to be executed. Execution proceeds by fetching, decoding, and executing the opcode pointed to by the PC.

### 3. Determinism: The Requirement for Universal Agreement

The stack-based architecture and fixed opcode costs are necessary to achieve **Determinism**. Determinism means that, given the same starting state and the same transaction input, every node running the EVM must produce the exact same resulting state. This eliminates uncertainty and ensures that the entire decentralized network agrees on the final outcome of any smart contract execution, transforming Ethereum into a reliable "World Computer".

### 4. EVM Runtime Life Cycle

The execution of a transaction within the EVM involves a structured cycle:

1. **Fetch:** The EVM reads the next opcode indicated by the Program Counter.
2. **Decode:** It identifies the operation (e.g., addition, memory write).
3. **Execute:** It performs the operation (e.g., popping values off the stack, performing math, reading from Storage).
4. **Gas Consumption:** A specific amount of gas is deducted for that operation.
5. **State Update:** Results are pushed back onto the stack, and, if applicable, Memory or persistent Storage is updated.

### Visual Aids & Analogies

### Analogy: The City Planner (Determinism)

Imagine a complex legal process that must produce a single, non-negotiable result (the final state). If multiple city planners, working independently, start with the same documents (initial state) and follow the exact same, clearly defined procedures (the EVM opcodes), they must all arrive at the same final blueprint and cost assessment. The EVM's strict, stack-based logic acts as that procedural mandate, forcing deterministic results across the world.

### Visual Aid: The LIFO Stack

![EVM Stack Operation - ADD Instruction.png](attachment:8fb23c30-73ac-47fc-8e9b-92efde855da3:EVM_Stack_Operation_-_ADD_Instruction.png)

### Practical Exercises

**Exercise 1.1: Tracing the Stack with Opcodes**

1. Students analyze a small sequence of opcodes, such as `PUSH1 0x04`, `PUSH1 0x05`, `ADD`, `PUSH1 0x01`, `MUL`.
2. They manually track the contents of the stack after each operation, noting how intermediate values are used and discarded.

### Class Discussion Prompts

1. **Isolation:** Why must the EVM be an **isolated** environment? How would allowing a contract to access random external variables (like a computer's CPU clock) violate the principle of determinism and break consensus?
2. **The EVM Analogy:** The EVM is often compared to the Java Virtual Machine (JVM). What core differences exist between the EVM and a typical virtual machine, given that the EVM prioritizes *determinism and scarcity* (via gas) over raw processing power?