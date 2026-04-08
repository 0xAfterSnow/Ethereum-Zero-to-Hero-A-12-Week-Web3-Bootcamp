# Week 4 – Introduction to Solidity and Structure

# 4.0 Week Overview

This week marks the pivotal shift from theory to tangible development as we dive into **Solidity**, the primary object-oriented, high-level language used for writing smart contracts on the Ethereum Virtual Machine (EVM). We will establish the foundation for writing production-ready code, focusing specifically on modern, secure practices using **Solidity 0.8.x**. This version is mandated due to its built-in safety features that automatically guard against common, costly vulnerabilities. 

We will master the structural components of a contract, focusing on data management (Structs, Mappings), execution control (Functions, Visibility, Modifiers), and the critical art of **Event Logging**. Proper event logging is not merely a logging feature; it is the fundamental architectural component that allows external services (like frontends and data indexers) to efficiently track and interpret state changes on the blockchain.

## 4.1 Weekly Learning Objectives

By the end of this week, students will be able to:

1. **Write Modern Solidity:** Confidently write secure, idiomatic Solidity contracts using the `pragma solidity ^0.8.0` directive, leveraging automatic overflow checks.
2. **Manage Complex State:** Utilize `structs`, `mappings`, and nested mappings to model and store complex, persistent contract data efficiently.
3. **Control Execution Flow:** Define functions with correct visibility (`public`, `external`, `internal`, `private`) and implement custom access control using function `modifiers` (e.g., `onlyOwner`).
4. **Implement Error Handling:** Use `require` for input validation and state checks, `revert` for complex error handling, and understand the role of `assert` for internal consistency checks.
5. **Master Event Logging:** Define and emit `events` to provide transparent, low-cost information about state changes to external dApps and indexing services.

[Day 1: Contract Structure and State Management](https://www.notion.so/Day-1-Contract-Structure-and-State-Management-288b304da65b80df84fcfdc7b6fcd2e8?pvs=21)

[Day 2: Functions, Control Flow, and Access Modifiers](https://www.notion.so/Day-2-Functions-Control-Flow-and-Access-Modifiers-288b304da65b80d6bf53f134f42c35f4?pvs=21)

[Day 3: Advanced Data Structures: Mappings and Error Handling](https://www.notion.so/Day-3-Advanced-Data-Structures-Mappings-and-Error-Handling-288b304da65b808fab5ddf2b6a1403c6?pvs=21)

[Day 4: Events, Logging, and The Secure Counter Milestone](https://www.notion.so/Day-4-Events-Logging-and-The-Secure-Counter-Milestone-288b304da65b80a49c8feac349d879c1?pvs=21)