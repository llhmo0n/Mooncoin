# Moonvault Quickstart Guide

## Installation

```bash
git clone https://github.com/llhmo0n/Moonvault.git
cd Moonvault
cargo build --release
```

## First Steps

### 1. Check Installation

```bash
./target/release/moonvault --help
```

### 2. View Status

```bash
./target/release/moonvault status
```

### 3. Check Gas Balance

```bash
./target/release/moonvault gas-balance
```

### 4. Run Node (to mine gas)

```bash
./target/release/moonvault run
```

Press `Ctrl+C` to stop.

## Creating a Vault

### Step 1: Generate Keys

```bash
./target/release/moonvault btc-lock-keygen
```

Save the hot, cold, and recovery keys.

### Step 2: Generate Invoice

```bash
./target/release/moonvault fee-invoice vault-create --pubkey <YOUR_PUBKEY>
```

### Step 3: Pay Invoice

Send the required BTC to the Fee Pool address shown.

### Step 4: Verify Payment

```bash
./target/release/moonvault fee-verify <BITCOIN_TXID> --invoice <INVOICE_ID>
```

### Step 5: Create Vault

```bash
./target/release/moonvault vault-create \
  --invoice <INVOICE_ID> \
  --hot-key <HOT_PUBKEY> \
  --cold-key <COLD_PUBKEY> \
  --recovery-key <RECOVERY_PUBKEY> \
  --timelock <BLOCK_HEIGHT>
```

## Important Reminders

⚠️ **Moonvault is NOT money**
- Gas units have no value
- BTC is the only economic asset
- Service fees are paid in BTC

🔐 **Backup your keys**
- Without recovery key, you cannot recover BTC after timelock
- Store keys securely offline
