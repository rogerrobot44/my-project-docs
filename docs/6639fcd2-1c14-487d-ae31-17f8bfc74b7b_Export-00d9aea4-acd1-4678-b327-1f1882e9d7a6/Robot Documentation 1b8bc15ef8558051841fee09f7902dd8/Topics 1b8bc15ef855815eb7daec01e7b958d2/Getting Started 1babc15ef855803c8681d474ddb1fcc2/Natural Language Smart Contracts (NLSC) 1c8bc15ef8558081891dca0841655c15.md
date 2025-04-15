# Natural Language Smart Contracts (NLSC)

---

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

---

---