# Primitives and Policies

### Each Natural Language Smart Contract (NLSC) is composed of:

- Primitives - atomic units of blockchain functionality (e.g., transfer, mint, condition, delay, vote)
- Policy - a higher-level specification that defines how and when primitives can be triggered, combined, or constrained

Together, these two layers form a contract that is both expressive and modular. Rather than encoding complex workflows in procedural code, developers or AI agents define intent through composable logic and policy in natural language.

For example, an NLSC might be:
“Every Friday, distribute 80% of collected protocol fees to contributors in proportion to their approved work, and retain 20% in the treasury.”

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

---