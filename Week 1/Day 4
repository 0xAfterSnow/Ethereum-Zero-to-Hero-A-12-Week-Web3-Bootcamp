## Day 4: Ethereum Accounts and the Transaction Lifecycle

### Day Topic & Subtopics

**EOAs, Digital Signatures, and The Gas Model**

1. Externally Owned Accounts (EOA) and Address Derivation
2. Digital Signatures: Authentication and Non-Repudiation (ECDSA)
3. The Ethereum Transaction Structure
4. EIP-1559: The Modern Gas Fee Model (Base Fee, Tip, Burning)

### Lecture Notes

### 1. Externally Owned Accounts (EOA)

The Externally Owned Account (EOA) is the primary user-controlled entity on Ethereum, often associated with wallet software like MetaMask. EOAs are controlled by a private key held by an external entity (the user), not by smart contract code.

- **Key Derivation Process:** The entire EOA identity originates from a highly random 256-bit number (the Private Key). This key mathematically derives the Public Key (via Elliptic Curve Cryptography), and the Public Key is then hashed (Keccak-256) to produce the final 40-character (20-byte) Ethereum address.
- **Security Control:** The private key is the ultimate custodian. Whoever holds the private key controls the associated funds and assets. Generating an EOA does not require a transaction or fee; it can be done entirely offline.

### 2. Digital Signatures and Non-Repudiation

When an EOA wishes to execute a transaction (send tokens, interact with a contract), the transaction data must be cryptographically **signed** using the EOA's private key. This is done using the Elliptic Curve Digital Signature Algorithm (ECDSA).

- **Authentication:** The signature is a cryptographic proof that the user possesses the private key for the sending address, thereby authenticating the sender.
- **Integrity and Non-Repudiation:** The signature is generated over the message digest (the hash) of the transaction data. If a single element of the transaction is tampered with, the signature becomes invalid, ensuring data integrity. Furthermore, once signed, the sender cannot deny having authorized the transaction—a property called non-repudiation.
- **Verification:** Network validators receive the signed transaction and use the sender’s public key to verify that the signature was legitimately created by the corresponding private key, without ever needing access to the private key itself.

The security model of the EOA, relying on a single, static private key for absolute control, is fundamentally the primary obstacle to achieving true Web3 mass adoption. Mainstream users expect centralized recovery mechanisms (like password reset flows), which are incompatible with the concept of absolute private key custody. This high-friction, single-point-of-failure model forces developers to pursue architectural solutions, such as Account Abstraction, to enable flexible security policies like social recovery, thus decoupling asset control from the single cryptographic key.

### 3. EIP-1559: The Modern Gas Model

Before the London hard fork in August 2021, Ethereum gas fees relied on a volatile, unpredictable first-price auction. EIP-1559 replaced this with a hybrid system that stabilizes costs and introduced a key change in monetary policy.

Transaction fees are paid to cover the computation required to execute the transaction. Under EIP-1559, fees have three core components:

- **Gas Limit:** The maximum amount of computational units the user is willing to allow the transaction to consume.
- **Base Fee:** An algorithmically determined, mandatory fee for each unit of gas. This fee adjusts automatically based on network congestion, aiming to keep blocks at 50% capacity. Crucially, the Base Fee is **burned** (permanently destroyed), constricting the total supply of ETH.
- **Priority Fee (Tip):** An optional extra payment the user can include. This tip is paid directly to the validator (staker) to incentivize them to prioritize the transaction over others during times of congestion.
- **Max Fee:** The maximum total price the user is willing to pay per unit of gas (covering both Base Fee and Tip). Any difference between the actual transaction cost and the Max Fee is refunded to the user, enhancing predictability.

EIP-1559 performs a strategic dual function: it improves the user experience by stabilizing gas prices from block to block , and it structurally reinforces ETH's value proposition. By directly linking network utility (congestion) to asset scarcity (burning), periods of high usage necessarily lead to a higher rate of ETH supply reduction. This creates an economic feedback loop where network activity reinforces ETH’s deflationary pressure and monetary appeal.

### Code Examples

We will conceptually review the signing process using a sample `ethers.js` function, noting that the private key handles the signing, while the public key's hash (the address) is used for verification.

```jsx
// Conceptual demonstration of signing flow using Ethers.js
// Private keys are loaded into a Wallet object for signing transactions/messages.

const { Wallet } = require('ethers');

// **WARNING**: NEVER hardcode real private keys. This is for conceptual teaching only.
const privateKey = '0x1111111111111111111111111111111111111111111111111111111111111111'; 
const wallet = new Wallet(privateKey); 

async function signData() {
    // 1. Define the message/transaction hash to be signed
    const message = "I approve the transfer of 1 ETH from my account.";
    
    // 2. The wallet uses the private key internally to generate the signature
    const signature = await wallet.signMessage(message); 

    console.log(`EOA Address (Verifier): ${wallet.address}`);
    console.log(`Original Message: ${message}`);
    console.log(`Digital Signature (Proof of Ownership): ${signature}`);

    // The network will then use wallet.address (public key derived) to verify this signature.
}

signData();
```

### Visual Aids & Analogies

### Analogy: EIP-1559 as a Taxi Ride

This analogy simplifies the fee structure:

- **Base Fee (Burned):** This is the mandatory, published city tariff for the ride. It fluctuates based on city traffic (network congestion). The money is collected by the city (burned) to maintain infrastructure.
- **Priority Fee (Tip):** This is the optional cash tip you give the driver (validator) to incentivize them to drive faster, ensuring they pick you up quickly.
- **Max Fee:** This is the budget cap you set before the ride begins. You are guaranteed a refund if the actual cost is lower.

### Visual Aid: The Key Derivation Funnel

![Ethereum Address Generation Flowchart.png](attachment:023781de-3104-4523-891b-b1e410c5d109:Ethereum_Address_Generation_Flowchart.png)

This visual reinforces that the entire digital identity traces back to the initial random private key.

### Practical Exercises

**Exercise 4.1: Analyzing Transaction Components**

1. Students review a recent transaction on Etherscan that occurred after the London hard fork.
2. Identify the `Gas Used`, `Base Fee per Gas`, `Priority Fee`, and the total `Max Fee per Gas` specified by the sender.
3. Calculate how much ETH was burned and how much was paid to the validator for that specific transaction.

### Class Discussion Prompts

1. **Non-Repudiation in Legal Context:** How does the cryptographic non-repudiation property of the signature compare to traditional legal processes, such as notarization or wet signatures, and what advantages does it offer in speed and verification?
2. **Validator Revenue:** Under EIP-1559, validators only receive the Priority Fee and the fixed block reward. How does the burning of the Base Fee affect the long-term profitability and security model for validators, especially compared to the pre-1559 era where they received 100% of all transaction fees?

### Summary Tables for Week 1

The following tables summarize the core foundational concepts covered in Week 1.

Web2 vs. Web3 Paradigm Shift

| **Aspect** | **Web 2.0 (Platform-Centric)** | **Web 3.0 (User-Centric/Blockchain)** |
| --- | --- | --- |
| **Data Ownership** | Owned by the platform/company | Owned by the individual (Self-sovereignty) |
| **Trust Model** | Trust is mediated by a central authority | Trustless; established by cryptography and consensus |
| **Identity/Login** | Centralized, siloed accounts | Decentralized Wallets (EOA keys) |
| **Censorship** | Prone to censorship | Less prone to censorship (network controlled) |

EIP-1559 Transaction Fee Components

| **Fee Component** | **Description** | **Recipient** | **Monetary Impact** |
| --- | --- | --- | --- |
| **Gas Limit** | Max computation units allowed. | N/A (limit only) | Controls max transaction complexity. |
| **Base Fee** | Algorithmically adjusted minimum price per gas unit. | Burned (destroyed from supply) | Creates deflationary pressure on ETH supply. |
| **Priority Fee (Tip)** | Optional fee for faster inclusion. | Validator (Staker) | Incentivizes transaction prioritization. |
| **Max Fee** | User's absolute maximum price ceiling. | N/A (limit only) | Guarantees predictability and refund eligibility. |
