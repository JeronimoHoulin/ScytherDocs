# Scyther Thesis

## Objectives

1. **Generate Alpha**
   - Chase yield in DeFi above benchmark (Aave & Lido APYs)
   - Farm points
   - Auto-compound returns back into the same vault

2. **Minimize Trust**
   - Architecture permits anyone to withdraw funds before permission changes are executed
   - Deposits & withdrawals are settled weekly
   - New permissions are executed with a one-month delay and notice on the TG channel
   - This gives users 4 windows to propose changes and/or exit

---

## Architecture

The system is built around two Safe multisigs with a strict permission boundary between them.

```
Safe A "The Vault"  ──►  Roles Modifier  ──►  Safe B "The Operator"
    (holds funds)          (enforces rules)        (executes strategy)
```

> [Zodiac Roles Modifier](https://docs.roles.gnosisguild.org/) enforces the permission boundary between Vault and Operator.

### Safe A — The Vault
Holds 100% of capital. Any transaction not explicitly pre-approved by the Roles Modifier will revert — the operator cannot execute outside the defined scope.

### Roles Modifier
A contract deployed by Safe A that grants Safe B a narrowly scoped set of permissions. Nothing outside those permissions can happen — not even if Safe B is compromised. See the [Zodiac Roles Modifier docs](https://docs.roles.gnosisguild.org/) for implementation details.

### Safe B — The Operator
Executes the strategy, rebalances, and disassembles as needed. Can perform pre-approved actions only.

### Tom — The Agent
Tom holds a [**Proposer**](https://help.safe.global/en/articles/235770-proposers) role within Safe B. This means it can queue transactions into Safe B's execution queue, but cannot execute anything unilaterally. AI speeds up operations without introducing unilateral control.

---

## Trust Model

Because the Operator needs the Vault's approval before interacting with any new protocol, pool, or contract, the following conditions govern how new permissions are granted:

| # | Condition |
|---|-----------|
| 1 | New permissions are publicly announced in the Telegram channel **"Permission Proposals"** |
| 2 | A **30-day waiting period** must pass between a proposal and its execution |
| 3 | The Vault settles every **7 days**, giving users **4 withdrawal windows** to exit before any new permission takes effect |

> No new capital exposure can be introduced without public notice and a meaningful window for users to withdraw if they disagree.

---

## The Farms

Scyther will launch with USD & ETH denominated farms.

### scyUSD

| Field | Value |
|---|---|
| Underlying asset | USDC |
| Entry chain | Ethereum mainnet |
| Exit chain | Ethereum mainnet |

### scyETH

| Field | Value |
|---|---|
| Underlying asset | WETH |
| Entry chain | Ethereum mainnet |
| Exit chain | Ethereum mainnet |

> Vaults can move assets cross-chain, but always under the same address custody — assets never leave the vault.
