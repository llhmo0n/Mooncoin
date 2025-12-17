# Moonvault Security Model

## Core Principle

**Your BTC is always recoverable.**

Moonvault is designed so that even if the entire Moonvault network disappears, you can still recover your Bitcoin directly on Bitcoin L1.

## Vault Architecture

### Three-Key System

| Key | Purpose | Restrictions |
|-----|---------|--------------|
| **Hot Key** | Daily operations | Limited to daily amount |
| **Cold Key** | Large transactions | Requires delay period |
| **Recovery Key** | Emergency recovery | Requires timelock expiration |

### Security Layers

```
Layer 1: Hot Key (daily spending)
├── Limited amount per day
├── Immediate transactions
└── If compromised: limited damage

Layer 2: Cold Key (savings)
├── No daily limit
├── Requires delay (e.g., 144 blocks = ~24h)
├── Can be cancelled during delay
└── If compromised: delay gives time to react

Layer 3: Recovery Key (emergency)
├── Full access to funds
├── Only works after timelock expires
├── Ultimate backup if other keys lost
└── If compromised: timelock protects until expiry
```

## Panic Button

If you detect unauthorized activity:

1. **Activate panic**: `moonvault vault-panic <VAULT_ID> --recovery-key <KEY>`
2. **All operations freeze immediately**
3. **Wait for timelock**
4. **Recover with recovery key**

## What Moonvault Cannot Do

- ❌ Access your BTC
- ❌ Move your BTC
- ❌ Block your recovery (after timelock)
- ❌ Change your vault rules
- ❌ Seize your funds

## Recovery Guarantee

```
INVARIANT: BTC is always recoverable on Bitcoin L1

Scenario: Moonvault completely disappears
Solution:
1. Wait for your timelock block height
2. Construct recovery transaction manually
3. Sign with your recovery key
4. Broadcast to Bitcoin network
5. Your BTC is recovered

No dependency on Moonvault for final recovery.
```

## Best Practices

### Key Storage

| Key | Storage Recommendation |
|-----|----------------------|
| Hot Key | Hardware wallet or encrypted on device |
| Cold Key | Hardware wallet (separate device) |
| Recovery Key | Paper/metal backup in secure location |

### Timelock Selection

| Timelock | Use Case |
|----------|----------|
| ~52,560 blocks (1 year) | Long-term savings |
| ~26,280 blocks (6 months) | Medium-term |
| ~4,380 blocks (1 month) | Active trading |

### Monitoring

- Check vault status regularly
- Set up alerts for vault activity
- Keep recovery key backup current

## Reporting Vulnerabilities

**DO NOT** open public issues for security vulnerabilities.

1. Contact maintainer directly
2. Provide detailed description
3. Allow 90 days for fix before disclosure

## Audit Status

Moonvault v4.0 has not been formally audited. Use at your own risk.

---

**Remember:** Moonvault is infrastructure, not money. Your security ultimately depends on your key management.
