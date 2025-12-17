# Changelog

All notable changes to Moonvault will be documented in this file.

## [4.0.0] - 2024-12-17

### 🔄 Major Rebrand
- **Renamed from Mooncoin to Moonvault**
- New identity: "Bitcoin Security Infrastructure"
- Clear messaging: "Protecting your Bitcoin, not replacing it"

### ⚠️ Critical Changes
- **Gas is NOT money**: Non-transferable, burn-only, no monetary value
- **Halving disabled**: No artificial scarcity (`HALVING_ENABLED = false`)
- **Max supply removed**: `MAX_SUPPLY = u64::MAX` (gas is unlimited)
- **Warning banner**: Every command shows "Moonvault is NOT money"

### ✨ New Features

#### Fee System (`fee_system.rs`)
- Generate BTC invoices for services
- Verify payments via Esplora API
- Fee Pool status tracking
- Distribution rules: 70% nodes, 20% maintenance, 10% reserve

#### Vault Service (`vault_service.rs`)
- Create security vaults with hot/cold/recovery keys
- Daily limits for hot key operations
- Delays for cold key withdrawals
- Panic button to freeze operations
- Recovery timelock for emergencies

#### New Commands
- `fee-invoice` - Generate payment invoice
- `fee-verify` - Verify BTC payment
- `fee-pool-status` - Show Fee Pool balance
- `vault-create` - Create security vault
- `vault-status` - Check vault status
- `vault-panic` - Activate panic button
- `vault-list` - List your vaults
- `gas-balance` - Show gas balance (with warning)

### 🔧 Technical Changes
- Network magic: `[0x4D, 0x56, 0x4C, 0x54]` ("MVLT")
- Binary name: `moonvault`
- Package name: `moonvault`
- New constants in `lib.rs` for fees and gas burns

### 📚 Documentation
- Updated README with anti-altcoin messaging
- New CONTRIBUTING.md
- Clear "What Moonvault NEVER Does" section

---

## [3.x and earlier] - Legacy Mooncoin

Previous versions operated under the "Mooncoin" name with different tokenomics. Version 4.0 represents a complete architectural shift to Bitcoin security infrastructure.

**Note:** If you have legacy "Mooncoin" from earlier versions, it has been converted to non-transferable gas units with no monetary value.
