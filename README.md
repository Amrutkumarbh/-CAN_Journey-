# Introduction to Vehicle Networking

> Part of my **CAN Bus Learning Journey** — notes, experiments, and projects as I go deeper into automotive embedded systems.

This section covers the foundational "why" before diving into CAN protocol specifics.

## Notes in This Section

| File | What's Covered |
|------|---------------|
| [01 — What is Vehicle Networking?](./01_what_is_vehicle_networking.md) | ECUs, point-to-point wiring problem, why ECUs need to talk |
| [02 — Early Networks & Why We Needed Better](./02_early_networks_and_problems.md) | Wiring chaos, advantages of networking, proprietary protocols (J1850, CCD, VAN, I-Bus) and their limitations |

## Key Takeaway

A modern car has 50–150+ ECUs that cannot work in isolation. Pre-network vehicles ran kilometres of wire — heavy, expensive, and impossible to scale. Proprietary solutions from each OEM made things worse. This set the stage for **CAN bus** as the universal automotive networking standard.

---
# Vehicle Network Technologies

> Part of my **CAN Bus Learning Journey** — notes, experiments, and projects as I go deeper into automotive embedded systems.

This section covers the 5 major vehicle network protocols and how they coexist inside a modern car.

## Notes in This Section

| File | What's Covered |
|------|---------------|
| [03 — CAN & LIN](./03_can_and_lin.md) | CAN basics (Bosch, ISO 11898, multi-master), LIN (single master, body comfort, gateway connection) |
| [04 — FlexRay, MOST & Automotive Ethernet](./04_flexray_most_automotive_ethernet.md) | Time-deterministic FlexRay, optical-fiber MOST, and the rise of Automotive Ethernet |
| [05 — Gateway ECU & Why CAN Won](./05_gateway_ecu_and_why_can_won.md) | How all networks connect via Gateway ECU, and the 5 reasons CAN dominates |

## Key Takeaway

A modern vehicle runs **multiple networks simultaneously**, each chosen for its job:
- **CAN** → the reliable backbone (powertrain, safety)
- **LIN** → cheap and slow (comfort, body)
- **FlexRay** → deterministic timing (x-by-wire)
- **MOST** → multimedia (being replaced)
- **Automotive Ethernet** → the fast future (ADAS, cameras, OTA)

The **Gateway ECU** is the translator sitting in the middle, bridging all these worlds together.

---
# CAN Protocol — Deep Dive

> Part of my **CAN Bus Learning Journey** — notes, experiments, and projects as I go deeper into automotive embedded systems.

This section gets into the actual mechanics of how CAN works — physical wiring, frame structure, and the clever arbitration mechanism.

## Notes in This Section

| File | What's Covered |
|------|---------------|
| [06 — CAN Physical Layer](./06_can_physical_layer.md) | Nodes, twisted pair, CAN_H/CAN_L, terminating resistors, why twisting kills noise, internal CAN node structure |
| [07 — CAN Frame Structure & Logic Levels](./07_can_frame_and_logic_levels.md) | SOF, Arbitration, Control, Data, CRC, ACK, End of Frame fields; Dominant vs Recessive logic |
| [08 — CAN Identifier & Arbitration](./08_can_identifier_arbitration.md) | How multi-master arbitration works bit-by-bit, worked example with ECU1 vs ECU2, why lower ID = higher priority |

## Key Takeaway

CAN's physical robustness comes from **differential signalling on twisted pair** (kills noise by 100×) and **terminating resistors** (prevents reflections). Its protocol robustness comes from **dominant/recessive logic** + **non-destructive bitwise arbitration** — the highest-priority message always wins, automatically, in hardware, without ever corrupting the bus.

---

*Previous section: [Vehicle Network Technologies](../vehicle_network_technologies/)*  
*Source: Personal handwritten notes — learning in progress 🚗*
