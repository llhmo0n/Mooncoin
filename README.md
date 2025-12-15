# 🌙 Mooncoin

**La plata digital — Bitcoin 2009 style in Rust 2025**

```
    ╔══════════════════════════════════════════════════════════════╗
    ║                                                              ║
    ║     ███╗   ███╗ ██████╗  ██████╗ ███╗   ██╗                 ║
    ║     ████╗ ████║██╔═══██╗██╔═══██╗████╗  ██║                 ║
    ║     ██╔████╔██║██║   ██║██║   ██║██╔██╗ ██║                 ║
    ║     ██║╚██╔╝██║██║   ██║██║   ██║██║╚██╗██║                 ║
    ║     ██║ ╚═╝ ██║╚██████╔╝╚██████╔╝██║ ╚████║                 ║
    ║     ╚═╝     ╚═╝ ╚═════╝  ╚═════╝ ╚═╝  ╚═══╝                 ║
    ║                                                              ║
    ║          El dinero que no se puede perder                    ║
    ║                                                              ║
    ╚══════════════════════════════════════════════════════════════╝
```

---

## ¿Qué es Mooncoin?

Mooncoin es una criptomoneda diseñada para **proteger a humanos**, no solo para transferir valor. 

Mientras Bitcoin resolvió el problema de "¿cómo enviar dinero sin intermediarios?", Mooncoin resuelve los tres problemas que han causado la pérdida de miles de millones en crypto:

| Problema | Solución Mooncoin |
|----------|-------------------|
| 🔐 **Robo** | Vaults con tiempo de espera |
| 🔑 **Pérdida de llaves** | Recuperación social |
| ⚰️ **Muerte del dueño** | Herencia programada |

---

## Características

### Núcleo (Bitcoin-compatible)
- ⛏️ Proof of Work (SHA-256d)
- 📦 Modelo UTXO
- 📜 Sistema de scripts (no Turing-completo)
- 🔢 21,000,000 MOON máximo
- ⏱️ Bloques cada 5 minutos
- 📉 Halving cada 210,000 bloques

### Protección Humana (Único en Mooncoin)
- 🏦 **Vaults** — Fondos con período de espera antes de poder gastar
- 🤝 **Recuperación Social** — Recupera acceso con ayuda de contactos de confianza
- 👨‍👩‍👧 **Herencia** — Transferencia automática tras inactividad prolongada

### Privacidad
- 🕵️ Direcciones stealth (receptor oculto)
- 🔮 Pedersen commitments (montos ocultos)
- 💍 Ring signatures (emisor oculto)
- 🌿 Dandelion++ (IP oculta)

### Avanzado
- ⚡ Payment Channels (pagos instantáneos off-chain)
- 🔄 Atomic Swaps (intercambios cross-chain)
- 📝 Smart Contracts (scripts avanzados)
- 🌳 Merkle Trees (verificación SPV)

---

## Instalación

### Requisitos
- Rust 1.70+
- 2GB RAM mínimo
- 10GB espacio en disco

### Compilar desde fuente

```bash
# Clonar repositorio
git clone https://github.com/llhmo0n/Mooncoin.git
cd Mooncoin

# Compilar
cargo build --release

# El binario estará en target/release/mooncoin
```

---

## Uso Rápido

### Iniciar nodo y minar
```bash
./target/release/mooncoin run
```

### Ver tu dirección
```bash
./target/release/mooncoin address
```

### Ver balance
```bash
./target/release/mooncoin balance
```

### Enviar MOON
```bash
./target/release/mooncoin send <dirección> <cantidad>
```

### Estado de la blockchain
```bash
./target/release/mooncoin status
```

---

## Comandos Disponibles

| Comando | Descripción |
|---------|-------------|
| `run` | Iniciar nodo y minar |
| `balance` | Ver balance de la wallet |
| `send <to> <amount>` | Enviar MOON |
| `status` | Estado de la blockchain |
| `address` | Mostrar tu dirección |
| `new-seed` | Crear nueva wallet HD |
| `restore <phrase>` | Restaurar wallet desde frase |
| `peers` | Ver peers conectados |
| `mempool` | Ver transacciones pendientes |
| `validate` | Validar blockchain completa |

### Comandos Avanzados
| Comando | Descripción |
|---------|-------------|
| `privacy-keygen` | Generar claves de privacidad |
| `stealth-demo` | Demo de direcciones stealth |
| `shielded-demo` | Demo de transacciones privadas |
| `contracts-demo` | Demo de smart contracts |
| `channels-demo` | Demo de payment channels |
| `atomic-swaps-demo` | Demo de atomic swaps |

---

## Especificaciones Técnicas

```
Algoritmo:           SHA-256d (doble SHA-256)
Tipo:                Proof of Work
Suministro máximo:   21,000,000 MOON
Recompensa inicial:  50 MOON por bloque
Halving:             Cada 210,000 bloques
Tiempo de bloque:    5 minutos (objetivo)
Ajuste dificultad:   Cada 2016 bloques
Madurez coinbase:    100 bloques
Prefijo dirección:   M (legacy), mc1 (SegWit)
Puerto P2P:          38333
Puerto RPC:          38332
Puerto Explorer:     38080
```

---

## Arquitectura

```
mooncoin/
├── src/
│   ├── main.rs          # Entry point y CLI
│   ├── lib.rs           # Constantes y utilidades
│   ├── block.rs         # Estructuras de bloque
│   ├── transaction.rs   # Transacciones
│   ├── wallet.rs        # Wallet básica
│   ├── hdwallet.rs      # Wallet HD (BIP39/BIP32)
│   ├── utxo.rs          # Set de UTXOs
│   ├── validation.rs    # Validación de consenso
│   ├── network.rs       # P2P networking
│   ├── mempool.rs       # Pool de transacciones
│   ├── privacy/         # Sistema de privacidad
│   ├── contracts.rs     # Smart contracts
│   ├── channels.rs      # Payment channels
│   └── atomic_swaps.rs  # Atomic swaps
├── docs/
│   ├── MOONCOIN_PROTOCOL_SPECIFICATION_v1.0.txt
│   ├── GUIA_DE_SUPERVIVENCIA.txt
│   ├── COMO_IDENTIFICAR_MOONCOIN_FALSO.txt
│   └── CARTA_DEL_CREADOR.txt
└── README.md
```

---

## Documentación

| Documento | Descripción |
|-----------|-------------|
| [Especificación del Protocolo](docs/MOONCOIN_PROTOCOL_SPECIFICATION_v1.0.txt) | Especificación técnica completa |
| [Guía de Supervivencia](docs/GUIA_DE_SUPERVIVENCIA.txt) | Cómo mantener Mooncoin vivo |
| [Identificar Mooncoin Falso](docs/COMO_IDENTIFICAR_MOONCOIN_FALSO.txt) | Cómo detectar fraudes |
| [Carta del Creador](docs/CARTA_DEL_CREADOR.txt) | Mensaje del creador |

---

## Principios Fundamentales

### 🚫 Sin Pre-mine
El bloque génesis tiene recompensa 0. Nadie tiene ventaja inicial.

### 🚫 Sin Fundación
No hay organización central. El código es la ley.

### 🚫 Sin Gobernanza On-chain
Los cambios se hacen por consenso social, no por votación.

### ✅ Código Abierto
MIT License. Usa, modifica, distribuye libremente.

### ✅ Verificable
Cualquiera puede verificar toda la blockchain desde el génesis.

---

## Cómo Identificar el Mooncoin Real

Si alguien te ofrece "Mooncoin 2.0" o similar, verifica:

1. ✅ Bloque génesis con coinbase = 0
2. ✅ Max supply = 21,000,000 exacto
3. ✅ PoW SHA-256d (no PoS, no DPoS)
4. ✅ Modelo UTXO (no cuentas)
5. ✅ Sin pre-mine
6. ✅ Sin fundación o autoridad central

Si falla cualquiera de estos puntos, **no es Mooncoin**.

---

## Contribuir

Mooncoin es software libre. Contribuciones bienvenidas:

1. Fork el repositorio
2. Crea una rama (`git checkout -b feature/nueva-cosa`)
3. Commit (`git commit -m 'Agregar nueva cosa'`)
4. Push (`git push origin feature/nueva-cosa`)
5. Abre un Pull Request

### Áreas que necesitan trabajo
- [ ] Más pruebas unitarias
- [ ] Documentación en inglés
- [ ] GUI wallet
- [ ] Mobile wallet
- [ ] Pool de minería

---

## Preguntas Frecuentes

### ¿Por qué otra criptomoneda?
Bitcoin es excelente para transferir valor, pero millones de dólares se pierden cada año por robo, pérdida de llaves, y muerte de los dueños. Mooncoin intenta resolver estos problemas humanos.

### ¿Es compatible con Bitcoin?
Comparte muchos conceptos (PoW, UTXO, scripts) pero no es un fork de Bitcoin. Es código nuevo escrito en Rust.

### ¿Dónde compro MOON?
Mooncoin no está en exchanges. La única forma de obtener MOON es minando o recibiéndolo de alguien que mine.

### ¿Quién creó Mooncoin?
Un desarrollador anónimo que cree que las criptomonedas deberían proteger a las personas, no solo su dinero.

---

## Licencia

MIT License — Haz lo que quieras con este código.

```
Copyright (c) 2025 Mooncoin Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

---

## Enlaces

- 📁 **Código fuente:** https://github.com/llhmo0n/Mooncoin
- 📜 **Especificación:** [docs/MOONCOIN_PROTOCOL_SPECIFICATION_v1.0.txt](docs/MOONCOIN_PROTOCOL_SPECIFICATION_v1.0.txt)

---

<div align="center">

**Mooncoin: El dinero que no se puede perder**

*Si en 10 años una sola persona recuperó sus fondos con Recuperación Social,*
*heredó crypto de un familiar fallecido con Herencia,*
*o canceló un robo gracias a un Vault...*

*Habrá valido la pena.*

🌙

</div>
