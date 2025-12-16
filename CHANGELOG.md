# Changelog

Todos los cambios notables de este proyecto serán documentados en este archivo.

---

## [3.0.0] - 2024-12-15 - PROTOCOLO CONGELADO

### El Puente con Bitcoin
- **Módulo BTC Lock completo** - Implementación del modelo LOCK-OPERATE-SETTLE
  - Generación de scripts LOCK (multisig_cltv, htlc_simple)
  - Observación de Bitcoin via Esplora API
  - Settlement TX Builder con firma ECDSA
  - 15 comandos CLI para gestión completa

- **Conexión a Bitcoin real**
  - Mainnet, Testnet, Signet soportados
  - Consulta de transacciones y UTXOs
  - Verificación de confirmaciones

### Estado del Protocolo
- Protocolo declarado CONGELADO
- No se agregarán más features
- Especificación es autoridad final

---

## [2.0.0] - 2024-12-14

### Core Blockchain
- Blockchain Mooncoin funcional
- Consenso Proof-of-Work (SHA-256d)
- Modelo UTXO completo
- Ajuste de dificultad cada 2016 bloques

### Wallet
- HD Wallet (BIP39/BIP32)
- Direcciones Legacy, SegWit, P2SH
- Encriptación AES-256-GCM
- Sistema de backup JSON

### Protección Humana
- Vaults con cancel path
- Recovery Social (3-of-5)
- Herencia Digital con timelock

### Privacidad
- Dandelion++ para propagación anónima
- Stealth Addresses
- Ring Signatures (demo)
- Shielded Transactions (demo)

### Red P2P
- Protocolo TCP custom
- Peer discovery
- Bootstrap nodes

### Smart Contracts
- Bitcoin Script compatible
- Multisig nativo
- Timelocks (CLTV, CSV)
- HTLCs para atomic swaps

---

## [1.0.0] - 2024-12-13

### Inicio
- Estructura inicial del proyecto
- CLI básico con clap
- Primeros módulos core

---

## Líneas Rojas (NUNCA violar)

- ❌ Cambiar supply máximo (21M)
- ❌ Proof of Stake
- ❌ Modelo de cuentas
- ❌ VM Turing-complete
- ❌ Pre-mine o ICO
- ❌ Gobernanza on-chain
- ❌ Tesorería controlada
- ❌ Custodiar BTC en el puente
