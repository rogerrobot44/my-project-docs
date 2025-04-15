# The Robot Wallet

## Overview

The Robot Wallet is the primary user interface to the Robot Network, allowing users to explore the Robot Network, deploy contracts and perform transactions via an AI chat interface. 

## Connecting your wallet

If don’t have a crypto wallet and need help on how to install and connect you wallet, here are links to the most popular web based crypto wallets:

- [MetaMask](https://support.metamask.io/start/getting-started-with-metamask/)
- [Rabby Wallet](https://support.rabby.io/hc/en-us/sections/11150481899663-Getting-Started)
- [Coinbase Wallet](https://www.coinbase.com/wallet/articles/getting-started-mobile)
- [Okx Wallet](https://www.okx.com/learn/how-to-create-an-okx-wallet)

All the examples in the following documentation will be using MetaMask. Other wallets have very similar functionality.

Ensure you have successfully installed your MetaMask wallet in the Google Chrome Extension.

Once the wallet web extension is installed, click “Connect MetaMask Wallet” and agree to connect your wallet to the Robot Network.

## Available Contract Types

Natural Language Smart Contracts (NLSCs) are the foundational units of logic and policy within the Robot Blockchain. They represent a fundamental shift from opaque bytecode to human-legible, semantically structured contracts that can be composed, inspected, and reasoned over in natural language.

### **Supported Contract Types (Out of the Box)**

These are default, pre-configured contract templates that come with the chain:

- **ERC-20 Token**
    
    Supports minting, burning, transferring, and balance tracking.
    
- **Automated Market Maker (AMM)**
    
    Supports liquidity deposit/withdrawal, token swaps, and price quoting.
    
- **Staking**
These are implemented by composing supported **Primitives** (see below), and are known to the chain by default.
- **Oracle**
    - Enables contracts to reference off-chain events, data, or states through **verified data feeds**.
    - Oracle-based contracts can subscribe to **pre-registered off-chain sources**, and access data (e.g., real-world prices, timestamps, outcomes) via special `readOracle` primitives.
    - All oracle reads must reference known data sources to ensure **deterministic, auditable execution**.

## Primitives and Policies

**Each Natural Language Smart Contract (NLSC) is composed of:**

- **Primitives** - atomic units of blockchain functionality (e.g., transfer, mint, condition, delay, vote)
- **Policies** - a higher-level specification that defines how and when primitives can be triggered, combined, or constrained

Together, these two layers form a contract that is both expressive and modular. Rather than encoding complex workflows in procedural code, developers or AI agents define intent through composable logic and policy in natural language.

For example, an NLSC might be:
*“Every Friday, distribute 80% of collected protocol fees to contributors in proportion to their approved work, and retain 20% in the treasury.”*

The primitives involved might include: time trigger, payment, proportional split, treasury logic, and work verification. The policy governs when and how these execute together.

Users can specify their desired actions and governing policies in a single natural language prompt; the Robot Wallet automatically parses out the Policies, Primitives and conditions.

### **Primitives**

Primitives are the low-level, chain-native operations that can be composed into new behaviors. Examples include:

- `mint`
- `burn`
- `transfer`
- `increaseCounter`
- `depositLiquidity`
- `quotePrice`
- `swapTokens`
- `readOracle`

These primitives are **explicitly supported** and validated by the Robot Chain runtime.

### Policies

Primitives such as the ERC-20 and AMM primitives will support policies at key locations.

Policy is when the user customizes a contract where the primitive allows customization.  Examples:

- ERC20 pre-transfer policy: Allows specific ERC20 contracts to require recipient to be compliant to preconditions such as KYC, or restriction of small transfers, etc.
- ERC20 mint policy: Allows minting until the supply exceeds 1 million, or only allow small minting, etc.
- AMM conditional swaps: Only allowing swaps of certain size limit, certain characteristics of the swappers, certain token balances, etc.

Future policy enhancements will allow policies to become more powerful and generalized.  V1 will only support policies that limit certain actions via true/false return value.  Future policies will allow actions to be taken, new state to be tracked that was not anticipated by the primitive writer, and the ability to receive new transaction or method calls to do new behaviors (long-term).

Callbacks is the term indicating a chunk of natural language that can be evaluated independently of the larger prompt it was a part of.  It can be posted into a newly deployed contract as a policy to evaluate whenever the policy is triggered, or it can be passed directly to a method for other uses (eg Flash Loan Callbacks).

## The Robot Copilot

### Overview

The Robot Copilot is a powerful AI-powered interface built around a multi-billion parameter language model, specifically fine-tuned for the Robot Blockchain environment. It serves as your intelligent assistant, enabling natural language interactions to query blockchain state, deploy contracts, and execute transactions. The Copilot understands smart contracts, orchestrations, and real-time state data through the Natural Language Index (NLI), providing a seamless bridge between user intent and blockchain execution.

### Getting Started

The Copilot interface integrates directly with your crypto wallet, ensuring all interactions are secure and authenticated. When you first connect, your wallet is embedded into the interface, and all intents generated through the Copilot are cryptographically signed before submission to the network. This preserves security while wrapping complex blockchain operations in an intuitive, conversational interface.

### Address Book

### Prompt Authoring

The Copilot accepts natural language prompts to execute blockchain operations. Whether you're asking about current DAO votes or creating automated payment systems, the Copilot translates your expressions into structured intents that can be executed on the blockchain. The system is bounded by the contents of the NLI, ensuring all recommendations are based on actual blockchain state rather than assumptions.

### Prompt Authoring: Identifying Wallet Addresses

Through the Address Book feature, the Copilot helps manage and identify wallet addresses by allowing you to assign memorable names to cryptographic addresses. This makes transactions more intuitive, as you can reference saved addresses by their custom names rather than dealing with long hexadecimal strings.

To identify a wallet address by name, simply type an at sign (@) to type-ahead the name of the wallet. The Copilot will automatically and securely translate that specific name into the appropriate hexadecimal string. 

### Prompt Authoring: Identifying Contracts

The Wallet ensures easy and unambiguous interactions with ERC-20 contracts by translating the Contract names into their hexadecimal strings automatically. To identify an address by name, in the prompt box simply type an a hash sign (#) to type-ahead the name of the contract.

### Sample Prompts

Below are three  simple sample prompts that include the main building blocks of the Robot Copilot: Natural language, Wallet identification, Contract identification, Policies and Transactions.

- "Show me the current balance of @AliceWallet"
- "Deploy a new AMM contract with a maximum swap size of 1000 tokens"
- "Transfer 100 tokens from #TokenContract to @DAOTreasury”

Block Explorer

Available Fields

Logs

Search