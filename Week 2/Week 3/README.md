# 3.0 Week Overview

Having covered the foundational architecture and consensus mechanisms of the network, Week 3 shifts our focus inward to the **Ethereum Virtual Machine (EVM)** the heart of the network. We will dissect the EVM's role as a deterministic, isolated operating environment for smart contracts. Understanding the EVM is crucial because it governs execution, performance, and, most importantly, cost. 

We will perform a deep dive into the EVM's stack-based machine architecture and its three primary data management areas: Stack, Memory, and the highly expensive persistent Storage. Finally, we will master the **Gas Mechanism** the economic engine that meters computational work, prevents denial-of-service attacks, and determines the real-world cost of your decentralized application (dApp) logic, explicitly analyzing the components of the EIP-1559 fee structure.

## 3.1 Weekly Learning Objectives

By the end of this week, students will be able to:

1. **Understand EVM Function:** Explain the EVM's role as a deterministic, stack-based environment for executing smart contract bytecode.
2. **Differentiate Data Locations:** Articulate the purpose, persistence, and relative gas costs of the EVM's core components: Stack, Memory, and persistent Storage.
3. **Analyze Gas Mechanics:** Define Gas, explain its necessity for mitigating spam, and calculate transaction fees based on `Gas Used`, `Base Fee`, and `Priority Fee` (EIP-1559).
4. **Evaluate Opcode Costs:** Develop an intuition for why certain Solidity operations (especially writing to storage) are exponentially more expensive than others, by examining the underlying opcodes.
5. **Simulate Execution:** Use the Remix IDE to analyze a simple contract's execution flow and identify operations that lead to an "Out-of-Gas" error.

[Day 1: The Ethereum Virtual Machine (EVM) Runtime](https://www.notion.so/Day-1-The-Ethereum-Virtual-Machine-EVM-Runtime-288b304da65b80f98da8f7aea4f397a0?pvs=21)

[Day 2: The EVM's Data Landscape: Storage, Memory, and Stack](https://www.notion.so/Day-2-The-EVM-s-Data-Landscape-Storage-Memory-and-Stack-288b304da65b8045aa2dc2f2556d358d?pvs=21)

[Day 3: The Gas Mechanism (EIP-1559 Deep Dive)](https://www.notion.so/Day-3-The-Gas-Mechanism-EIP-1559-Deep-Dive-288b304da65b8054a56fd176ca3c7546?pvs=21)

[Day 4: Hands-on EVM Interaction and Deployment Analysis](https://www.notion.so/Day-4-Hands-on-EVM-Interaction-and-Deployment-Analysis-288b304da65b80fd9f44c2a2d2ab039a?pvs=21)
