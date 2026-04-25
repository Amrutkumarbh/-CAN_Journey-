# 06 — CAN Physical Layer

> **Personal notes from my CAN learning journey** — transcribed from handwritten notes, Page 6

---

## Terminology

- **Node** — any communicating electronic device on the bus (sensors, actuators, ECUs)
- **SAE** — Society of Automotive Engineers (standards body)

---

## Physical Layer: Two Twisted Lines

CAN uses a **twisted pair** cable with two wires:

- **CAN_H** (CAN High)
- **CAN_L** (CAN Low)

### Bus Topology with Terminating Resistors

```
120Ω                                              120Ω
 ├──────────────────────────────────────────────────┤
 │  CAN_H ════╦════════════╦════════════════════════╣
 │            ║            ║
 │  CAN_L ════╩════════════╩════════════════════════╣
              │            │
           ┌──┴──┐      ┌──┴──┐
           │ ECU │      │ ECU │
           └─────┘      └─────┘
```

> **Terminating Resistors:** Typically **120Ω** at each end of the bus.  
> Combined equivalent resistance across the bus = ~**60Ω**.  
> Without them, signals reflect from the ends → errors and reduced reliability.

---

## Why Twisted Pair?

Any external magnetic field (from a nearby motor wire, ignition cable) induces a voltage in a wire loop. By twisting:

- Each **half-twist** creates a loop in one direction
- The **next half-twist** creates a loop in the **opposite** direction
- The induced voltages **cancel each other out** over the length of the cable

> **Key result:** Twisted pair reduces inductively coupled noise by **100×** compared to parallel wires.

```
CAN_H  ─╲╱─╲╱─╲╱─╲╱─╲╱─╲╱─╲╱─╲╱─
CAN_L  ─╱╲─╱╲─╱╲─╱╲─╱╲─╱╲─╱╲─╱╲─
         (twisted around each other every few cm)
```

---

## Inside a CAN Node

```
              ┌───────────────────────────┐
  CAN_H/L ──→ │     CAN Receiver          │ → Converts analog signal to logical 0 / 1
              ├───────────────────────────┤
              │        ↑↓ 0s/1s           │
              │     CAN Controller        │ → Handles framing, arbitration, error logic
              ├───────────────────────────┤
              │          ↑↓               │
              │          ECU              │ → Application logic
              └───────────────────────────┘
```

---

*Previous: [05 — Gateway ECU & Why CAN Won](../vehicle_network_technologies/05_gateway_ecu_and_why_can_won.md)*  
*Next: [07 — CAN Frame Structure & Logic Levels](./07_can_frame_and_logic_levels.md)*
