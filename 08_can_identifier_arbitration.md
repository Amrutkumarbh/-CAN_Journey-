# 08 — CAN Identifier & Arbitration

> **Personal notes from my CAN learning journey** — transcribed from handwritten notes, Page 8

---

## CAN Arbitration — How Collisions Are Avoided

CAN is a **multi-master bus** — any node can transmit at any time. But what happens when two nodes try to transmit **simultaneously**?

CAN solves this with **non-destructive bitwise arbitration**, using the CAN ID in the Arbitration Field.

---

## How It Works — Step by Step

Every node transmits its CAN ID **bit by bit, MSB first**, and simultaneously **reads back** what's on the bus.

- If a node sends a **Recessive (1)** but reads back **Dominant (0)** → another node with a lower ID is transmitting → **it loses arbitration and stops immediately**
- The **winner** (lowest ID) never even knows a collision happened — it just keeps transmitting

---

## Worked Example

```
         SOF │ Arbitration Field
─────────────┼──────────────────────────────
ECU 1    0   │  0 1 1 0 0 1 0 1 1 1 0
ECU 2    0   │  0 1 1 1 0 1 1 1 1 1 0
─────────────┼──────────────────────────────
                        ↑
              Bit 4: ECU1 sends 0 (Dominant)
                     ECU2 sends 1 (Recessive)
                     Bus = 0 (Dominant wins)

              ECU2 reads back 0, but sent 1
              → ECU2 STOPS and starts listening
              → ECU1 wins and continues
```

> **ECU1's ID = 0110 0101 110** (lower value)  
> **ECU2's ID = 0111 0111 110** (higher value)  
> Lower ID → higher priority → wins arbitration

---

## Key Properties of CAN Arbitration

| Property | Detail |
|----------|--------|
| **Non-destructive** | The winning message is never corrupted |
| **Automatic** | No software needed — pure hardware logic |
| **Deterministic** | The highest-priority message **always** wins |
| **No wasted time** | Loser backs off instantly — no re-transmission delay for the winner |
| **No single point of failure** | Multi-master means any node can take over |

---

## Why This Matters for Safety Systems

In a crash scenario, the **airbag ECU** needs its message to reach the bus immediately. By giving it the **lowest CAN ID**, it always wins arbitration over lower-priority messages like mirror adjustments — guaranteed by hardware, not software.

---

*Previous: [07 — CAN Frame Structure & Logic Levels](./07_can_frame_and_logic_levels.md)*
