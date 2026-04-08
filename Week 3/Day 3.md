# Day 3: The Gas Mechanism (EIP-1559 Deep Dive)

## Day Topic & Subtopics

**Economic Engine: Measuring and Paying for Computation**

1. Gas Definition and Purpose: The Unit of Work
2. Gas Units vs. Gwei vs. ETH
3. EIP-1559 Structure: Base Fee, Priority Fee, and Burning
4. Out-of-Gas Errors: Reversion and Payment

### Lecture Notes

### 1. Gas Definition and Purpose

**Gas** is the unit of measure for the computational effort expended to execute operations on the EVM. Every opcode (e.g., `ADD`, `SSTORE`) has a fixed gas cost.

- **Purpose:** Gas is essential for security and economic incentive.
    1. **DOS Prevention:** By requiring payment for computation, gas prevents malicious actors from launching Denial-of-Service (DoS) attacks (e.g., infinite loops) that would stall the network.
    2. **Validator Compensation:** It compensates validators for the computational resources they expend to process and verify transactions.

### 2. Gas Units vs. Gwei vs. ETH

It is critical to distinguish between the three terms used for transaction costs:

- **Gas Units:** The *quantity* of computational work needed (e.g., 21,000 units for a simple ETH transfer).
- **Gas Price (Gwei):** The *price* paid for each unit of gas, denominated in Gwei (Giga-wei, or 109 wei).
- **ETH:** The total currency paid, calculated as:
    
    Total ETH Fee=Gas Units Used×Gas Price
    

### 3. EIP-1559 Structure

The London hard fork introduced EIP-1559, changing the fee model from a first-price auction to a hybrid system with predictable fees and a deflationary mechanism.

- **Base Fee Per Gas:** This is an algorithmically determined, mandatory minimum fee for including a transaction in the current block. It dynamically adjusts based on network congestion, rising if the previous block was over 50% full (by up to 12.5%) and decreasing if it was under 50% full.
    - **Crucially, the Base Fee is burned (permanently destroyed), removing ETH from circulation.**.
- **Max Priority Fee Per Gas (Tip):** This is an optional extra fee paid directly to the validator to incentivize them to prioritize the transaction over others in the mempool.
- **Max Fee Per Gas:** The absolute maximum amount the user is willing to pay per unit of gas (covering both the Base Fee and the Tip). Any difference between the actual required fee and the Max Fee is refunded to the sender, ensuring predictability.

### 4. Out-of-Gas Errors

Every transaction must specify a **Gas Limit**—the maximum amount of gas the user is willing to spend.

- **Failure:** If the EVM executes an operation that causes the consumed gas to exceed the Gas Limit, an **"Out-of-Gas" error** occurs.
- **Reversion:** When this happens, all state changes made by the transaction are instantly reverted (the Global State is not changed).
- **Payment:** Even though the transaction failed and was reverted, the sender **still pays the full amount of gas consumed** up to the limit. This design ensures validators are compensated for their work, regardless of the outcome.

### Visual Aids & Analogies

### Analogy: EIP-1559 as a Bus Fare

- **Base Fee (Burned):** The standard, non-negotiable bus fare set by the city (network). It ensures everyone pays the base cost of running the service. This cash is shredded after collection (burned).
- **Priority Fee (Tip):** The optional tip you hand directly to the driver (validator) to incentivize them to wait an extra second for you or move your luggage faster.
- **Max Fee:** The absolute amount of cash in your hand you authorized the driver to take. Any unused amount is returned immediately.

### Practical Exercises

**Exercise 3.1: Gas Calculation**
Given the following variables, calculate the final cost to the user in ETH (using 1 Gwei = 10−9 ETH):

- Gas Used: 50,000 units
- Base Fee: 25 Gwei
- Max Priority Fee: 2 Gwei
- *Calculation:* Total Gas Price = Base Fee (25) + Priority Fee (2) = 27 Gwei. Total Cost = 50,000 × 27 Gwei = 1,350,000 Gwei or 0.00135 ETH.

### Class Discussion Prompts

1. **Deflationary Mechanism:** Discuss the long-term economic impact of the Base Fee burning. How does this mechanism affect the monetary policy of ETH, and why is this conceptually different from fees in a Proof-of-Work system?
2. **User Experience:** EIP-1559 aimed to improve UX by making fees predictable. Why is the ability for a wallet to accurately estimate the Base Fee important for mass adoption, compared to the old, volatile auction system?