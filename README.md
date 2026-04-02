Welcome to the ultimate bootcamp designed to forge the next generation of full-stack blockchain engineers. This curriculum is a rigorous, practical, and comprehensive journey from the foundational principles of Web3 to deploying sophisticated decentralized applications on the Ethereum blockchain.

## **🛠️ Part 0: Developer Environment & Tooling Setup**

Before we begin, it's crucial to set up a professional development environment. This one-time setup will serve you throughout the entire course.

### **Core Software:**

1. **Code Editor:** [Visual Studio Code](https://code.visualstudio.com/) is the industry standard.
2. **Version Control:** [Git](https://git-scm.com/downloads) for tracking code changes.
3. **Terminal:**
- **macOS:** Use the built-in Terminal or [iTerm2](https://iterm2.com/).
- **Windows:** Use [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/install) for a native Linux environment.
1. **Node.js & npm:** Install via [nvm (Node Version Manager)](https://github.com/nvm-sh/nvm). We'll use the latest LTS version.
    
    nvm install --lts
    
    nvm use --lts
    
2. **Blockchain Wallet:** [MetaMask](https://metamask.io/) browser extension. **Secure your seed phrase!**

### **VS Code Extensions:**

- **Hardhat for VSCode:** Official Hardhat language support.
- **Solidity by Nomic Foundation:** Provides real-time code analysis and compilation.
- **Prettier - Code formatter:** To keep your code clean and consistent.
- **ESLint:** To find and fix problems in your JavaScript/TypeScript code.

### **Essential Resources:**

- **Documentation:** [Ethereum.org](https://ethereum.org/en/developers/docs/), [Solidity Docs](https://docs.soliditylang.org/), [OpenZeppelin Docs](https://docs.openzeppelin.com/contracts), [Ethers.js Docs](https://docs.ethers.org/), [Wagmi Docs](https://wagmi.sh/).
- **Testnet Faucets:** Get free test ETH from sites like [Alchemy Faucet](https://www.alchemy.com/faucets/ethereum-sepolia) or [Infura Faucet](https://www.infura.io/faucet/sepolia).
- **Community:** Discord, Telegram, X

## **🗓️ The 12-Week Curriculum**

### **Module 1: Foundations of Decentralized Technology (Weeks 1-4)**

### **Week 1: The Web3 Revolution & Blockchain Fundamentals**

- **Learning Objectives:**
- Articulate the core value proposition of Web3 and decentralization.
- Explain how a blockchain works at a high level.
- Differentiate between Web2 and Web3 architectures.
- **Key Topics & Subtopics:**
- **What is Web3?** The evolution from Web1 to Web3, core concepts (decentralization, permissionless, trustless).
- **Blockchain 101:** What is a distributed ledger? Blocks, chains, and cryptographic hashing.
- **How Blockchains Work:** Nodes, peer-to-peer networks, consensus mechanisms (Proof-of-Work vs. Proof-of-Stake).
- **Cryptography Basics:** A gentle introduction to public/private key cryptography and digital signatures.
- **Hands-on Exercises:**
- Visually interact with a blockchain demo to see how blocks are mined and chained.
- Generate a public/private key pair using a simple tool.
- **Real-world Examples:** Bitcoin as the first blockchain, the concept of a decentralized internet.
- **Tools & Libraries:** Blockchain visualizer tools, online key generators.
- **Weekly Milestone:** Write a one-page summary explaining the difference between a centralized database and a blockchain to a non-technical audience.

### **Week 2: Ethereum Ecosystem Deep Dive**

- **Learning Objectives:**
- Describe the key components of the Ethereum network.
- Explain the function of the Ethereum Virtual Machine (EVM).
- Understand the lifecycle of an Ethereum transaction.
- **Key Topics & Subtopics:**
- **Introduction to Ethereum:** The "World Computer" vision.
- **The EVM:** How Ethereum executes code, opcodes, and the stack-based architecture.
- **Ethereum Accounts:** Externally Owned Accounts (EOAs) vs. Smart Contract Accounts.
- **Transactions & Gas:** Anatomy of a transaction (nonce, to, value, data), gas, gas limit, gas price, and the concept of gasless transactions.
- **Blocks & State:** How Ethereum's state is stored and updated via transactions.
- **Merkle Trees:** Understanding how they ensure data integrity.
- **Hands-on Exercises:**
- Use a block explorer like [Etherscan](https://etherscan.io/) to dissect a real transaction.
- Calculate the cost of a transaction based on gas price and gas used.
- **Real-world Examples:** Examining a transaction from a popular dApp like Uniswap on Etherscan.
- **Tools & Libraries:** Etherscan, MetaMask.
- **Weekly Milestone:** Create a detailed diagram illustrating the journey of a transaction from a user's wallet to its inclusion in a block.

### **Week 3: Wallets, Keys, and Account Abstraction**

- **Learning Objectives:**
- Securely manage a non-custodial wallet.
- Understand the relationship between keys, accounts, and seed phrases.
- Explain the concepts behind smart contract wallets and account abstraction (ERC-4337).
- **Key Topics & Subtopics:**
- **Wallet Deep Dive:** MetaMask setup and security best practices.
- **Keys & Seed Phrases:** The critical importance of the seed phrase (mnemonic).
- **WalletConnect:** How dApps connect to mobile wallets.
- **Introduction to Account Abstraction (AA):** Moving beyond EOAs.
- **ERC-4337:** The concepts of UserOperation, Bundler, Paymaster, and Entry Point contract.
- **Smart Contract Wallets:** Features like social recovery, batch transactions, and spending limits.
- **Hands-on Exercises:**
- Set up a new MetaMask wallet and back up the seed phrase securely.
- Connect to a dApp (like Uniswap) using both MetaMask and WalletConnect.
- Interact with a demo dApp that utilizes account abstraction for a gasless transaction.
- **Real-world Examples:** Argent, Safe, Sequence as leading smart contract wallets.
- **Tools & Libraries:** MetaMask, WalletConnect, dApps with AA integration.
- **Weekly Milestone:** Write a blog post comparing the user experience and security trade-offs between a standard EOA wallet (MetaMask) and a smart contract wallet.

### **Week 4: Your First Smart Contract with Solidity**

- **Learning Objectives:**
- Set up a local development environment with Hardhat.
- Write, compile, and deploy a basic Solidity smart contract.
- Interact with a deployed contract on a local blockchain.
- **Key Topics & Subtopics:**
- **Introduction to Smart Contracts:** "Code is law."
- **Anatomy of a Solidity File:** pragma, contract, state variables, functions.
- **Solidity Data Types:** uint, address, bool, string, bytes.
- **Functions:** Visibility (public, private, internal, external), state mutability (view, pure).
- **Introduction to Hardhat:** The professional Ethereum development environment.
- **Hands-on Exercises:**
- Initialize a new Hardhat project (npx hardhat init).
- Write a "SimpleStorage" contract that stores and retrieves a number.
- Write a Hardhat script to deploy the contract to a local network.
- Write a Hardhat task to interact with the deployed contract.
- **Real-world Examples:** The concept of a simple on-chain registry or notary.
- **Tools & Libraries:** Solidity 0.8+, Hardhat, Ethers.js (via Hardhat).
- **Weekly Milestone:** Create a "Greeter" smart contract that stores a greeting message. Deploy it and write a script to change and retrieve the greeting.

### **Module 2: dApp Development & Smart Contract Mastery (Weeks 5-8)**

### **Week 5: Intermediate Solidity**

- **Learning Objectives:**
- Implement complex data structures and control flows in Solidity.
- Understand contract inheritance and code reuse.
- Properly emit and listen for events.
- **Key Topics & Subtopics:**
- **Complex Data Types:** structs, mappings, arrays (fixed and dynamic).
- **Control Structures:** if/else, for loops.
- **Modifiers:** Reusable checks for function execution (onlyOwner).
- **Events:** Logging data on the blockchain for off-chain UIs to consume.
- **Inheritance & Interfaces:** Building modular and extensible contracts.
- **Libraries:** Reusable code for common patterns.
- **Error Handling:** require(), revert(), assert().
- **Hands-on Exercises:**
- Build a contract with a mapping to store user balances.
- Create an onlyOwner modifier and apply it to a function.
- Emit an event whenever a balance is updated.
- **Real-world Examples:** OpenZeppelin's Ownable.sol contract.
- **Tools & Libraries:** Hardhat, Solidity.
- **Weekly Milestone:** Build a simple multi-sig wallet contract that requires a minimum number of owners to approve a transaction before it can be executed.

### **Week 6: Token Standards (ERC20, ERC721) & NFTs**

- **Learning Objectives:**
- Explain the purpose and function of ERC token standards.
- Build, test, and deploy a fungible token (ERC20).
- Build, test, and deploy a non-fungible token (ERC721).
- Understand ERC1155 and its advantages.
- **Key Topics & Subtopics:**
- **Fungible vs. Non-Fungible Tokens.**
- **ERC20 Standard Deep Dive:** balanceOf, transfer, approve, transferFrom.
- **ERC721 Standard Deep Dive:** ownerOf, safeTransferFrom, token metadata.
- **ERC1155 Multi-Token Standard:** The best of both worlds.
- **Using OpenZeppelin Contracts:** The industry standard for secure, reusable contract implementations.
- **NFT Metadata:** Storing NFT data off-chain using IPFS.
- **Hands-on Exercises:**
- Create your own ERC20 token using OpenZeppelin's wizard and Hardhat.
- Create your own ERC721 NFT collection, complete with custom metadata.
- Upload NFT metadata to IPFS using a service like Pinata.
- **Real-world Examples:** USDC (ERC20), CryptoPunks (ERC721), Enjin (ERC1155).
- **Tools & Libraries:** OpenZeppelin Contracts, Hardhat, IPFS, Pinata.
- **Weekly Milestone:** Create and deploy your own unique NFT collection to a testnet. Verify the contract on Etherscan and view your NFTs on OpenSea's testnet site.

### **Week 7: Building the dApp Frontend**

- **Learning Objectives:**
- Set up a modern frontend project using React/Next.js.
- Connect a frontend application to the blockchain and user wallets.
- Read data from smart contracts and display it in the UI.
- **Key Topics & Subtopics:**
- **dApp Architecture:** How the frontend, wallet, RPC node, and smart contract interact.
- **Frontend Framework:** Setting up a project with Next.js.
- **Connecting to Ethereum:** Using **Ethers.js** as a provider.
- **Modern React Hooks for Web3:** Introduction to **Wagmi**, a powerful library for interacting with Ethereum.
- **Wallet Integration:** Using **RainbowKit** for a seamless, multi-wallet connection experience.
- **Reading Contract State:** Calling view and pure functions from the frontend.
- **Hands-on Exercises:**
- Create a new Next.js application.
- Integrate Wagmi and RainbowKit to add a "Connect Wallet" button.
- Display the connected user's address and ETH balance.
- Fetch and display the total supply of the ERC20 token created in Week 6.
- **Real-world Examples:** The frontend of any major dApp (e.g., Aave, Uniswap).
- **Tools & Libraries:** React, Next.js, Ethers.js, Wagmi, RainbowKit.
- **Weekly Milestone:** Build a frontend "dApp dashboard" that connects to your deployed ERC721 contract and displays the total number of NFTs minted and the NFTs owned by the connected user.

### **Week 8: Full-Stack dApp Integration & Testing**

- **Learning Objectives:**
- Execute state-changing transactions from a frontend application.
- Listen for smart contract events to update the UI in real-time.
- Write comprehensive tests for smart contracts.
- Introduce an alternative testing framework: **Foundry**.
- **Key Topics & Subtopics:**
- **Writing to Contracts:** Sending transactions that change the blockchain state.
- **Handling Transaction States:** Pending, success, and error states in the UI.
- **Listening to Events:** Updating the UI automatically when a contract event is emitted.
- **Smart Contract Testing with Hardhat:** Using Chai matchers for assertions.
- **Introduction to Foundry:** An alternative, Rust-based toolkit for testing in Solidity.
- **Unit Tests vs. Forking Tests.**
- **Hands-on Exercises:**
- Add a "mint" button to your NFT dApp frontend that allows users to mint a new NFT.
- Display a loading indicator while the transaction is pending and a success message upon completion.
- Write unit tests for your ERC721 contract, covering minting and transfer logic.
- (Bonus) Rewrite a simple Hardhat test using Foundry's testing style.
- **Real-world Examples:** The user experience of minting an NFT or swapping tokens on a DEX.
- **Tools & Libraries:** All tools from Week 7, plus Hardhat/Chai for testing, Foundry (optional).
- **Weekly Milestone:** Complete your full-stack NFT minting dApp. A user should be able to connect their wallet, see contract information, mint an NFT, and see their collection update in the UI.

### **Module 3: Advanced Topics, Security, & Deployment (Weeks 9-12)**

### **Week 9: Smart Contract Security & Auditing**

- **Learning Objectives:**
- Identify and prevent common smart contract vulnerabilities.
- Apply security best practices throughout the development lifecycle.
- Understand the basics of the smart contract auditing process.
- **Key Topics & Subtopics:**
- **The Hacker Mindset:** Thinking adversarially.
- **Common Vulnerabilities:** Reentrancy, integer overflow/underflow, front-running, access control flaws.
- **Security Best Practices:** Checks-Effects-Interactions pattern, using trusted libraries (OpenZeppelin), explicit visibility.
- **Auditing Tools:** Static analysis tools (Slither).
- **The Auditing Process:** What to expect when working with professional auditors.
- **Hands-on Exercises:**
- Analyze a vulnerable contract and perform a reentrancy attack on a local network.
- Refactor the vulnerable contract to fix the flaw.
- Run Slither on your own smart contracts to identify potential issues.
- **Real-world Examples:** The DAO Hack (reentrancy), the Parity Wallet Hack (access control).
- **Tools & Libraries:** Slither, Ethernaut (a Web3/Solidity security wargame).
- **Weekly Milestone:** Complete the first 5 levels of the Ethernaut wargame, documenting the vulnerability and solution for each.

### **Week 10: DeFi, Oracles, and Layer 2 Scaling**

- **Learning Objectives:**
- Explain the core building blocks of Decentralized Finance (DeFi).
- Describe the "oracle problem" and how solutions like Chainlink solve it.
- Understand why Layer 2 solutions are needed and how they work.
- **Key Topics & Subtopics:**
- **DeFi Primitives:** Tokens, staking, Decentralized Exchanges (DEXes), Automated Market Makers (AMMs), liquidity pools, lending/borrowing, flash loans.
- **Oracles:** The problem of getting real-world data on-chain.
- **Chainlink:** How it provides decentralized data feeds.
- **The Scalability Trilemma.**
- **Layer 2 (L2) Scaling Solutions:** A high-level overview of Polygon, Arbitrum, and Optimism (Optimistic vs. ZK-Rollups).
- **Gas Optimization Techniques:** Writing efficient Solidity code.
- **Hands-on Exercises:**
- Interact with a DEX like Uniswap on a testnet.
- Write a simple smart contract that consumes price data from a Chainlink Price Feed.
- Deploy one of your previous projects to an L2 testnet like Polygon Mumbai or Arbitrum Sepolia.
- **Real-world Examples:** Uniswap (DEX), Aave (Lending), Chainlink (Oracle), Arbitrum (L2).
- **Tools & Libraries:** Chainlink Contracts, L2 block explorers.
- **Weekly Milestone:** Build a simple "Token Staking" contract where users can deposit your ERC20 token and earn rewards over time.

### **Week 11: Professional Deployment & Data Indexing**

- **Learning Objectives:**
- Deploy and verify smart contracts on a public testnet and mainnet.
- Use an RPC provider for reliable network access.
- Build a subgraph to efficiently query blockchain data.
- **Key Topics & Subtopics:**
- **RPC Providers:** Why you need them (Alchemy, Infura, Sequence SDK).
- **Deployment & DevOps:** Writing robust Hardhat deployment scripts. Managing private keys securely.
- **Contract Verification:** Making your source code public on Etherscan for trust.
- **The Indexing Problem:** Why reading historical event data is difficult.
- **The Graph Protocol:** Building a subgraph to index your contract's events.
- **GraphQL:** Querying your subgraph data for use in the dApp frontend.
- **Hands-on Exercises:**
- Sign up for an Alchemy or Infura account.
- Modify your Hardhat config to deploy to the Sepolia testnet.
- Deploy and verify your NFT contract on Sepolia.
- Build and deploy a subgraph for your NFT contract that indexes Transfer events.
- Use the subgraph's GraphQL endpoint to fetch data for your dApp frontend instead of direct node calls.
- **Real-world Examples:** Most major dApps use The Graph to power their UIs.
- **Tools & Libraries:** Alchemy/Infura, The Graph, GraphQL.
- **Weekly Milestone:** Fully migrate your NFT dApp's data-fetching logic to use your newly created subgraph. The UI should now load much faster and be able to display a full history of mints.

### **Week 12: Final Capstone Project & Career Pathways**

- **Learning Objectives:**
- Architect, build, and deploy a complete, portfolio-worthy dApp from scratch.
- Demonstrate mastery of the full Web3 development stack.
- Prepare for a career in Web3.
- **Key Topics & Subtopics:**
- **Capstone Project Work:** Students work independently or in small groups on their chosen project track.
- **Project Management:** Defining scope, milestones, and deliverables.
- **Whitepaper:** Writing a short document explaining their project's purpose and architecture.
- **Portfolio Building:** How to showcase your projects effectively on GitHub.
- **The Web3 Job Market:** Roles, interview process, and networking.
- **Contributing to Open Source & DAOs.**
- **Hands-on Exercises:** Dedicated time for project development with instructor support.
- **Weekly Milestone:** **Deliver a Final Capstone Project.** This includes a live, deployed dApp, a public GitHub repository with a professional README, a short whitepaper, and a live demo presentation.

## **🎓 Final Capstone Project Options**

Students will choose one of three tracks to build a comprehensive final project.

### **1. NFT Marketplace Track**

- **Project:** A fully functional NFT marketplace.
- **Core Features:**
- Users can mint new NFTs from a collection contract.
- Users can list their minted NFTs for sale for a fixed price.
- Other users can browse and buy listed NFTs.
- A royalty fee is paid to the original collection creator on secondary sales.
- **Stack:** Solidity, OpenZeppelin, Hardhat, Next.js, Wagmi, The Graph, IPFS.

### **2. DeFi Protocol Track**

- **Project:** A staking and yield farming protocol.
- **Core Features:**
- Users can stake a base ERC20 token (e.g., a mock DAI).
- In return for staking, users earn a separate "reward" ERC20 token over time.
- Users can claim their rewards and unstake their original tokens at any time.
- A frontend dashboard shows staking stats like APY and total value locked.
- **Stack:** Solidity, OpenZeppelin, Hardhat, Next.js, Wagmi, Chainlink (for potential price data).

### **3. DAO & Governance Track**

- **Project:** A Decentralized Autonomous Organization (DAO) for a mock treasury.
- **Core Features:**
- An ERC20 governance token. Token holders can delegate their voting power.
- A treasury contract that holds funds.
- A governance contract where users can create and vote on proposals.
- If a proposal passes, it can be executed automatically (e.g., to send funds from the treasury).
- **Stack:** Solidity, OpenZeppelin (Governor & Timelock contracts), Hardhat, Next.js, Wagmi, The Graph.

[Meet the Instructor]()

[Week 1 – The Web3 & Blockchain Foundation](https://github.com/0xAfterSnow/Ethereum-Zero-to-Hero-A-12-Week-Web3-Bootcamp/tree/main/Week%201)

[Week 2 – Blockchain Architecture, Nodes, and Consensus]()

[Week 3 – The Ethereum Virtual Machine (EVM) and Gas]()

[Week 4 – Introduction to Solidity and Structure]()
