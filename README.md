# 🌙 MOONCOIN v3.0 — PROTOCOLO CONGELADO

## "El dinero que no se puede perder"

---

## ⚠️ AVISO IMPORTANTE

**Este protocolo está CONGELADO.**

No se agregarán features. No se optimizará sin emergencia criptográfica.
La especificación es la autoridad final.

---

## 📜 Documentos Fundacionales

| Documento | Propósito |
|-----------|-----------|
| `MOONCOIN_PROTOCOL_SPECIFICATION_v1.0.txt` | Define qué ES Mooncoin |
| `README.md` | Este archivo |
| `src/` | Implementación de referencia |

**La especificación tiene precedencia sobre el código.**

---

## 🎯 Qué es Mooncoin

Mooncoin es un sistema de dinero electrónico peer-to-peer que **complementa** a Bitcoin resolviendo tres problemas humanos:

| Problema | Solución Mooncoin |
|----------|-------------------|
| **Robo/Error** | Vaults con cancel path |
| **Pérdida de acceso** | Recovery social (3-of-5) |
| **Muerte del dueño** | Herencia digital automática |

Mooncoin **NO** es:
- Competidor de Bitcoin
- Plataforma de smart contracts
- Sistema con gobernanza
- Proyecto con fundación o tesorería

---

## 📊 Estado Final

```
┌─────────────────────────────────────────────────────────────┐
│                    MOONCOIN v3.0                            │
│                  PROTOCOLO CONGELADO                        │
├─────────────────────────────────────────────────────────────┤
│  Código:          ~27,000 líneas                            │
│  Módulos:         50+                                       │
│  Tests:           297 passing                               │
│  Estado:          COMPLETO - NO AGREGAR                     │
└─────────────────────────────────────────────────────────────┘
```

---

## 🔐 Parámetros Monetarios (INMUTABLES)

```
Supply máximo:          21,000,000 MOON
Decimales:              8
Recompensa inicial:     50 MOON
Halving cada:           210,000 bloques (~4 años)
Tiempo de bloque:       5 minutos
Ajuste dificultad:      Cada 2,016 bloques
Consenso:               Proof of Work (SHA-256d)
Modelo:                 UTXO
```

**Estos parámetros NUNCA cambian.**

---

## 🛡️ Protección Humana

### Vaults (vs robo)
```
Hot key → Inicia retiro → 24h espera → Completa
                ↓
        Detectas robo → Cold key → CANCELA → Recovery address
```

### Recovery Social (vs pérdida)
```
Pierdes seed → 3-of-5 guardianes firman → 30 días espera → Recuperas
                                              ↓
                          Apareces → CANCELAS con tu clave
```

### Herencia Digital (vs muerte)
```
Check-in cada 6 meses → Timer se resetea → Tú controlas
           ↓
No check-in por 1 año → Herederos reclaman automáticamente
```

---

## 🌐 Relación con Bitcoin

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│   BITCOIN (2009)                                                │
│   "Dinero que no se puede censurar"                            │
│   Oro digital. Store of value. Máxima seguridad.               │
│                                                                 │
│                         +                                       │
│                                                                 │
│   MOONCOIN (2024)                                               │
│   "Dinero que no se puede perder"                              │
│   Plata digital. Protección humana. Privacidad nativa.         │
│                                                                 │
│                         =                                       │
│                                                                 │
│   SISTEMA MONETARIO COMPLETO PARA HUMANOS                       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

Compatible vía Atomic Swaps. **Complementario, no competidor.**

---

## 🔗 BTC LOCK - El Puente con Bitcoin

El módulo BTC Lock implementa el puente **no-custodial** entre Mooncoin y Bitcoin.

### El Modelo LOCK-OPERATE-SETTLE

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│  1. LOCK    →  Usuario bloquea BTC en script con timelock       │
│                (El BTC permanece en Bitcoin, no en Mooncoin)    │
│                                                                 │
│  2. OPERATE →  Usuario opera con MOON libremente                │
│                (El BTC sigue intacto en Bitcoin)                │
│                                                                 │
│  3. SETTLE  →  Timelock expira, usuario recupera su BTC         │
│                (Con su clave de recovery, sin intermediarios)   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Principios del Puente

- **Mooncoin NUNCA custodia BTC** — Solo observa la blockchain
- **El usuario SIEMPRE controla sus claves** — Sin intermediarios
- **El BTC SIEMPRE puede ser recuperado** — Después del timelock
- **Sin confianza requerida** — Verificación criptográfica pura

### Comandos BTC Lock

```bash
# Verificación del sistema
mooncoin btc-lock-health          # Verificar todos los componentes
mooncoin btc-lock-connect         # Probar conexión a Bitcoin

# Generación de LOCKs
mooncoin btc-lock-templates       # Ver templates disponibles
mooncoin btc-lock-keygen          # Generar claves de prueba (testnet)
mooncoin btc-lock-generate        # Generar script LOCK
mooncoin btc-lock-verify          # Verificar script

# Gestión de LOCKs
mooncoin btc-lock-register        # Registrar LOCK
mooncoin btc-lock-status          # Ver estado de un LOCK
mooncoin btc-lock-list            # Listar todos los LOCKs
mooncoin btc-lock-refresh         # Actualizar estados

# Settlement
mooncoin btc-lock-settle-check    # Verificar si listo para settlement
mooncoin btc-lock-settle          # Construir TX de settlement

# Consultas Bitcoin
mooncoin btc-lock-query-tx        # Consultar transacción
mooncoin btc-lock-check-utxo      # Verificar UTXO
```

### Conexión a Bitcoin

| Red | API |
|-----|-----|
| Mainnet | blockstream.info/api |
| Testnet | blockstream.info/testnet/api |
| Signet | mempool.space/signet/api |

---

## 🚫 Líneas Rojas (Violar = No es Mooncoin)

- ❌ Cambiar supply máximo
- ❌ Proof of Stake
- ❌ Modelo de cuentas (debe ser UTXO)
- ❌ VM Turing-complete
- ❌ Pre-mine o ICO
- ❌ Gobernanza on-chain
- ❌ Tesorería controlada
- ❌ Eliminar privacidad por defecto
- ❌ Eliminar protecciones humanas
- ❌ Custodiar BTC en el puente

---

## 🔧 Uso

```bash
# Compilar
cargo build --release

# Tests
cargo test

# Ejecutar
./target/release/mooncoin

# Verificar BTC Lock
./target/release/mooncoin btc-lock-health
```

---

## 📁 Estructura del Proyecto

```
mooncoin/
├── src/
│   ├── main.rs        # CLI completo (~7,100 líneas)
│   ├── btc_lock.rs    # Módulo BTC Lock (~1,700 líneas)
│   └── lib.rs         # Constantes del protocolo
├── docs/
│   ├── MOONCOIN_PROTOCOL_SPECIFICATION_v1.0.txt
│   ├── BTC_LOCK.md
│   ├── SECURITY.md
│   └── QUICKSTART.md
├── Cargo.toml
├── README.md
├── CHANGELOG.md
└── LICENSE
```

---

## 📝 Para Futuros Mantenedores

1. **NO AGREGUEN FEATURES** — Mooncoin está completa
2. **NO OPTIMICEN SIN NECESIDAD** — Si funciona, no lo toquen
3. **NO CREEN GOBERNANZA** — El momento que hay votación, hay política
4. **NO BUSQUEN ADOPCIÓN** — Existe para quien la necesite
5. **MANTENGAN LA ESPECIFICACIÓN** — Es más importante que el código
6. **SEPAN DECIR NO** — El 99% de las ideas son malas
7. **EL PUENTE NUNCA CUSTODIA** — Mooncoin observa Bitcoin, nunca lo controla

---

## 🏛️ Ausencia del Creador

Este proyecto fue diseñado para sobrevivir sin su creador.

- No hay autoridad central
- No hay fundación
- No hay tesorería
- No hay poder especial para nadie

La especificación es la autoridad. El código la implementa.

**Si alguien dice hablar "en nombre de Mooncoin", miente.**

---

## 📄 Licencia

MIT — Usa, modifica, distribuye libremente.

---

*"El mejor dinero es el que nunca pierdes, ni siquiera cuando mueres."*

**Mooncoin v3.0 — Protocolo Congelado** 🌙
