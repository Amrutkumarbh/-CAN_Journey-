# 07 — CAN Frame Structure & Logic Levels

> **Personal notes from my CAN learning journey** — transcribed from handwritten notes, Page 7

---

## CAN Frame Structure

Every message on a CAN bus is sent inside a **frame**. The frame has a fixed structure:

```
┌─────┬─────────────┬─────────┬──────────────┬──────────┬─────┬───────────┐
│ SOF │ Arbitration │ Control │     Data     │   CRC    │ ACK │ End Frame │
│  1b │    Field    │  Field  │    Field     │  Field   │  2b │    7b     │
└─────┴─────────────┴─────────┴──────────────┴──────────┴─────┴───────────┘
```

### Field-by-Field Breakdown

| Field | Size | Purpose |
|-------|------|---------|
| **SOF** — Start of Frame | 1 bit | Marks the beginning of a message |
| **Arbitration Field** | 11-bit (std) or 29-bit (ext) | Contains the **CAN ID** — determines message priority |
| **Control Field** | Variable | Contains **Data Length Code (DLC)** — how many bytes follow (0–8) |
| **Data Field** | 0–8 bytes | The actual payload |
| **CRC Field** | 15 bits + delimiter | Cyclic Redundancy Check — error detection |
| **ACK Field** | 2 bits | Receiving nodes pull this dominant to acknowledge |
| **End of Frame** | 7 bits | Marks the end of the message |

> **CRC → Cyclic Redundancy Check** — a mathematical checksum computed over the frame. Any single-bit flip changes the CRC, catching the error.

---

### Arbitration Field Detail

```
┌─────────────────────────────────────┐
│   Arbitration Field                 │
│                                     │
│   CAN ID: Standard = 11 bits        │
│           Extended  = 29 bits       │
└─────────────────────────────────────┘
```

Lower CAN ID = **higher priority** (dominant bits win arbitration — see next page).

---

## Logic Levels: Dominant & Recessive

CAN uses **differential voltage** (CAN_H − CAN_L) to define logic:

| Logic | Name | Voltage Condition |
|-------|------|-------------------|
| **1** | **Recessive** | CAN_H − CAN_L ≈ **0V** (both at ~2.5V) |
| **0** | **Dominant** | CAN_H − CAN_L ≥ **1.5V** |

> **Why "Dominant"?**  
> If any node drives a **0 (Dominant)**, it overrides any node trying to send a **1 (Recessive)** — like a wired-AND. This is the physical foundation of CAN arbitration.

```
Recessive (Logic 1):   CAN_H ≈ 2.5V │ CAN_L ≈ 2.5V  →  Diff ≈ 0V
Dominant  (Logic 0):   CAN_H ≈ 3.5V │ CAN_L ≈ 1.5V  →  Diff ≈ 2V
```

---

*Previous: [06 — CAN Physical Layer](./06_can_physical_layer.md)*  
*Next: [08 — CAN Identifier & Arbitration](./08_can_identifier_arbitration.md)*
