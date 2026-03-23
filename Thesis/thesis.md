# Scyther — Strategy Thesis

## Objective

Generate alpha in DeFi by chasing yield, farming points, and auto-compounding returns back into the same vault.

---

## Architecture

The system is built around two Safe multisigs with a strict permission boundary between them.

```
Safe A "The Vault"  ──►  Roles Modifier  ──►  Safe B "The Operator"
    (holds funds)          (enforces rules)        (executes strategy)
```
> [Zodiac Roles Modifier](https://docs.roles.gnosisguild.org/) enforces the permission boundary between Vault and Operator.

### Safe A — The Vault

Holds 100% the capital. Any transaction that has not been explicitly pre-approved by the Roles Modifier will revert (the operator can't execute).

### Roles Modifier

A contract deployed by Safe A that grants Safe B a narrowly scoped set of permissions. Nothing outside those permissions can execute — not even if Safe B is compromised. See the [Zodiac Roles Modifier docs](https://docs.roles.gnosisguild.org/) for implementation details.

### Safe B — The Operator

Executes the strategy, rebalances and dissasembles as needed. Can perform pre-approved actions only.

### Tom — The AI Agent

Tom holds a [**Proposer**](https://help.safe.global/en/articles/235770-proposers) role within Safe B. This means he can queue transactions into Safe B's execution queue, but cannot execute anything unilaterally. He speeds up operations without introducing unilateral control.

---

## Trust Model

Because the Operator needs the Vault's approval before interacting with any new protocol, pool, or contract, the following conditions govern how new permissions are granted:

| # | Condition |
|---|-----------|
| 1 | New permissions are publicly announced in the Telegram channel **"Permission Proposals"** |
| 2 | A **30-day waiting period** must pass between a proposal and its execution |
| 3 | The Vault settles every **7 days**, giving users **4 withdrawal windows** to exit before any new permission takes effect |

This design ensures that no new capital exposure can be introduced without public notice and a meaningful window for users to withdraw if they disagree.
