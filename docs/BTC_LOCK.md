# Moonvault BTC Lock System

## Overview

The BTC Lock system allows Moonvault to **observe** Bitcoin transactions without ever taking custody. This is the foundation of Moonvault's security model.

## Key Principle

```
OBSERVE, NEVER CUSTODY

Moonvault watches your Bitcoin.
Moonvault never holds your Bitcoin.
```

## Lock Templates

### MultisigCLTV (Primary)

Used for vaults. Combines multisig with timelock:

```
IF
  2 <hot_pubkey> <cold_pubkey> 2 CHECKMULTISIG
ELSE
  <timelock> CHECKLOCKTIMEVERIFY DROP
  <recovery_pubkey> CHECKSIG
ENDIF
```

**Spending paths:**
1. **Normal**: Hot + Cold keys sign together (anytime)
2. **Recovery**: Recovery key signs (after timelock)

### HTLC Simple

Hash Time-Locked Contracts for atomic operations:

```
IF
  HASH256 <hash> EQUAL
  <receiver_pubkey> CHECKSIG
ELSE
  <timeout> CHECKLOCKTIMEVERIFY DROP
  <sender_pubkey> CHECKSIG
ENDIF
```

## Commands

### Generate Keys (testnet only)

```bash
moonvault btc-lock-keygen
```

### Generate Lock Script

```bash
moonvault btc-lock-generate \
  --pubkey-hot <HOT_KEY> \
  --pubkey-cold <COLD_KEY> \
  --pubkey-recovery <RECOVERY_KEY> \
  --timelock <BLOCK_HEIGHT> \
  --testnet
```

### Verify Script

```bash
moonvault btc-lock-verify <SCRIPT_HEX>
```

### Register Lock

```bash
moonvault btc-lock-register \
  --script <SCRIPT_HEX> \
  --txid <FUNDING_TXID> \
  --vout <OUTPUT_INDEX>
```

### Check Status

```bash
moonvault btc-lock-status <LOCK_ID>
```

### List All Locks

```bash
moonvault btc-lock-list
```

### Test Bitcoin Connection

```bash
moonvault btc-lock-connect
```

## Network Support

| Network | Esplora API |
|---------|-------------|
| Mainnet | blockstream.info |
| Testnet | blockstream.info/testnet |
| Signet | mempool.space/signet |

## P2WSH Addresses

Locks generate native SegWit (P2WSH) addresses:

- **Mainnet**: `bc1q...`
- **Testnet**: `tb1q...`

These are standard Bitcoin addresses. Any wallet can send to them.

## Settlement

When timelock expires, recover BTC with:

```bash
moonvault btc-lock-settle <LOCK_ID>
```

This generates a transaction you can broadcast to Bitcoin.

## Security Notes

1. **Keys stay with you**: Moonvault never sees your private keys
2. **Observation only**: We query Esplora API to check UTXO status
3. **No custody**: We cannot move your BTC
4. **Recovery guaranteed**: After timelock, you can always recover on L1

---

## Technical Details

### Address Generation

```rust
// Script to P2WSH address
let script_hash = sha256(script);
let address = bech32_encode("bc", script_hash);
```

### Timelock Encoding

```rust
// Block height encoding in script
if height < 500_000_000 {
    // Interpreted as block height
} else {
    // Interpreted as Unix timestamp
}
```

### Verification

Moonvault verifies scripts match expected templates before registering. Unknown scripts are rejected.
