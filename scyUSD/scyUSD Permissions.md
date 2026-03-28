## Live Permissions

View active Roles Modifier permissions via the Zodiac UI:

[Open in Safe → Zodiac](https://app.safe.global/apps/open?safe=eth:0x2C2e1c9c336bcB595B9f39720D30398a0e12E208&appUrl=https%3A%2F%2Fzodiac.gnosisguild.org%2F)

☝️ Might take a while to load, but press on the "view roles" button; 

<img width="391" height="237" alt="image" src="https://github.com/user-attachments/assets/e0517040-66b4-4559-8569-f3118e05e369" />


## Static recap:

# Neutrl / sNUSD Flow

---

## 🟢 Assemble

### 1. USDC → Approve Neutrl Router
| Field | Value |
|-------|-------|
| **Contract** | `0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48` |
| **Selector** | `0x095ea7b3` — `approve` |

### 2. Neutrl Router → Mint NUSD
| Field | Value |
|-------|-------|
| **Contract** | `0xa052883ebEe7354FC2Aa0f9c727E657FdeCa744a` |
| **Selector** | `0x52555702` — `mint` |

### 3. NUSD → Approve sNUSD
| Field | Value |
|-------|-------|
| **Contract** | `0xE556ABa6fe6036275Ec1f87eda296BE72C811BCE` |
| **Selector** | `0x095ea7b3` — `approve` |

### 4. sNUSD → Stake NUSD
| Field | Value |
|-------|-------|
| **Contract** | `0x08EFCC2F3e61185D0EA7F8830B3FEc9Bfa2EE313` |
| **Selector** | `0x6e553f65` — `deposit` |

---

## 🔴 Disassemble

### 1. sNUSD → Approve Instant Unstake
| Field | Value |
|-------|-------|
| **Contract** | `0x08EFCC2F3e61185D0EA7F8830B3FEc9Bfa2EE313` |
| **Selector** | `0x095ea7b3` — `approve` |

### 2. Instant Unstake → Unstake
| Field | Value |
|-------|-------|
| **Contract** | `0x4Bb8F67D5643e6289C55371DBFD021ddFdAEA0F6` |
| **Selector** | `0xbd0461aa` |

---

# CowSwap

### 1. CowSwap Swap
| Field | Value |
|-------|-------|
| **Contract** | `0x23dA9AdE38E4477b23770DeD512fD37b12381FAB` |
| **Selector** | `0x569d3489` — `signOrder` |

> **Swap out of any and all assets to:**
> `USDC` · `USDT` · `USDe` · `DUSD` · `avUSD`


### 2. NUSD → Approve CowSwap Order Signer
| Field | Value |
|-------|-------|
| **Contract** | `0xE556ABa6fe6036275Ec1f87eda296BE72C811BCE` |
| **Selector** | `0x095ea7b3` — `approve` |

### 3. USDC → Approve CowSwap Order Signer
| Field | Value |
|-------|-------|
| **Contract** | `0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48` |
| **Selector** | `0x095ea7b3` — `approve` |
