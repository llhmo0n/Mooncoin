# 🔐 Moonvault v4.0

## Bitcoin Security Infrastructure

> **"Protecting your Bitcoin, not replacing it."**

---

## ⚠️ IMPORTANT NOTICE

```
╔═══════════════════════════════════════════════════════════════════════════╗
║                                                                           ║
║   Moonvault is NOT money. It is infrastructure software.                  ║
║                                                                           ║
║   • 'Gas units' have NO monetary value                                    ║
║   • Gas is NOT transferable - burn only                                   ║
║   • BTC is the ONLY economic asset                                        ║
║   • Service fees are paid in BTC on Bitcoin L1                            ║
║                                                                           ║
║   If anyone tries to sell you gas units, they are scamming you.           ║
║                                                                           ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

---

## 🎯 What is Moonvault?

Moonvault provides **security services for Bitcoin self-custody**:

| Problem | Moonvault Solution |
|---------|-------------------|
| **Theft** | Vaults with hot/cold keys and panic button |
| **Human Error** | Delays and cancellation windows |
| **Key Loss** | Recovery paths with timelocks |

### What Moonvault is NOT:

- ❌ A cryptocurrency or digital money
- ❌ A competitor to Bitcoin
- ❌ An investment or store of value
- ❌ A token you can trade

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              BITCOIN L1                                     │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  • Your BTC (always here, never custodied by Moonvault)             │   │
│   │  • Fee Pool (service fees in BTC)                                   │   │
│   │  • Vault Scripts (P2WSH addresses)                                  │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                              ▲                                              │
│                              │ observes (never custodies)                   │
│                              │                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                         MOONVAULT                                   │   │
│   │  • Coordination layer (ordering events)                             │   │
│   │  • Service activation (after BTC payment)                           │   │
│   │  • Gas burning (anti-spam only)                                     │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────────┘
```

**INVARIANT:** If Moonvault disappears, you can ALWAYS recover your BTC directly on Bitcoin L1 using your keys + timelock.

---

## 📦 Installation

```bash
# Clone
git clone https://github.com/llhmo0n/Moonvault.git
cd Moonvault

# Build
cargo build --release

# Verify
./target/release/moonvault --help
```

### Requirements

- Rust 1.70+
- Linux/macOS/Windows (WSL)

---

## 🔧 Commands

### Fee System (BTC payments)

```bash
# Generate invoice for a service
moonvault fee-invoice vault-create --pubkey <YOUR_PUBKEY>

# Verify payment
moonvault fee-verify <BITCOIN_TXID> --invoice <INVOICE_ID>

# Check Fee Pool status
moonvault fee-pool-status
```

### Vault Services

```bash
# Create vault (after paying invoice)
moonvault vault-create \
  --invoice <INVOICE_ID> \
  --hot-key <HOT_PUBKEY> \
  --cold-key <COLD_PUBKEY> \
  --recovery-key <RECOVERY_PUBKEY> \
  --timelock <BLOCK_HEIGHT>

# Check vault status
moonvault vault-status <VAULT_ID>

# Activate panic button (freeze everything)
moonvault vault-panic <VAULT_ID> --recovery-key <PRIVKEY>

# List your vaults
moonvault vault-list
```

### Gas & Node

```bash
# Check gas balance
moonvault gas-balance

# Run node (mine gas)
moonvault run

# Show status
moonvault status
```

### BTC Lock System

```bash
# Show lock templates
moonvault btc-lock-templates

# Generate lock script
moonvault btc-lock-generate --pubkey-hot <KEY> --pubkey-cold <KEY> --pubkey-recovery <KEY> --timelock <HEIGHT>

# Check connection to Bitcoin
moonvault btc-lock-connect
```

---

## 💰 Fee Schedule

| Service | BTC Fee | Gas Burn |
|---------|---------|----------|
| Create Vault | 10,000 sats | 1 gas |
| Modify Vault | 5,000 sats | 1 gas |
| Monitoring (monthly) | 1,000 sats | 0 gas |

### Fee Distribution (immutable)

| Recipient | Percentage |
|-----------|------------|
| Node Operators | 70% |
| Protocol Maintenance | 20% |
| Security Reserve | 10% |

All distributions are on-chain in Bitcoin and publicly auditable.

---

## 🔐 Vault Security Model

### Three Keys

| Key | Purpose | Power |
|-----|---------|-------|
| **Hot Key** | Daily operations | Limited by daily amount |
| **Cold Key** | Large withdrawals | Requires delay period |
| **Recovery Key** | Emergencies | Full access after timelock |

### Panic Button

If you detect theft or compromise:

1. Activate panic with recovery key
2. All operations FREEZE immediately
3. Wait for timelock, then recover with recovery key

### Recovery Guarantee

```
YOUR BTC IS ALWAYS RECOVERABLE.

Even if Moonvault disappears completely:
1. Wait for timelock to expire
2. Use your recovery key
3. Spend directly on Bitcoin L1

Moonvault cannot prevent you from recovering your Bitcoin.
```

---

## ⛽ Gas System

**Gas is NOT money.** It exists only to prevent spam.

| Property | Value |
|----------|-------|
| Transferable | ❌ NO |
| Burnable | ✅ YES |
| Market Value | ❌ NONE |
| Purpose | Anti-spam only |

To get gas: Run a node with `moonvault run`

---

## 📁 Project Structure

```
moonvault/
├── src/
│   ├── main.rs           # CLI and commands
│   ├── lib.rs            # Protocol constants
│   ├── btc_lock.rs       # Bitcoin observation
│   ├── fee_system.rs     # BTC fee verification
│   ├── vault_service.rs  # Vault management
│   ├── wallet.rs         # Key management
│   ├── block.rs          # Block structure
│   ├── transaction.rs    # Transaction handling
│   └── ...
├── docs/
│   ├── BTC_LOCK.md
│   ├── SECURITY.md
│   └── QUICKSTART.md
├── Cargo.toml
└── README.md
```

---

## 🚫 What Moonvault NEVER Does

- ❌ Custody your BTC
- ❌ Move your BTC
- ❌ Create money or tokens with value
- ❌ Compete with Bitcoin
- ❌ Promise returns or profits
- ❌ Have governance over your funds

---

## 🛡️ Security

Found a vulnerability? Please report responsibly:

1. **DO NOT** open a public issue
2. Contact the maintainer directly
3. Allow time for a fix before disclosure

---

## 📜 License

MIT License - See [LICENSE](LICENSE)

---

## 👤 Author

**KNKI** - [GitHub](https://github.com/llhmo0n)

---

<div align="center">

**Moonvault v4.0**

*Bitcoin Security Infrastructure*

*Protecting your Bitcoin, not replacing it.*

🔐

</div>
