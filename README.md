# Introduction to Vehicle Networking

> Part of my **CAN Bus Learning Journey** — notes, experiments, and projects as I go deeper into automotive embedded systems.

This section covers the foundational "why" before diving into CAN protocol specifics.

## Notes in This Section

| File | What's Covered |
|------|---------------|
| [01 — What is Vehicle Networking?](./01_what_is_vehicle_networking.md) | ECUs, point-to-point wiring problem, why ECUs need to talk |
| [02 — Early Networks & Why We Needed Better](./02_early_networks_and_problems.md) | Wiring chaos, advantages of networking, proprietary protocols (J1850, CCD, VAN, I-Bus) and their limitations |
| [03 — CAN & LIN](./03_can_and_lin.md) | CAN basics (Bosch, ISO 11898, multi-master), LIN (single master, body comfort, gateway connection) |
| [04 — FlexRay, MOST & Automotive Ethernet](./04_flexray_most_automotive_ethernet.md) | Time-deterministic FlexRay, optical-fiber MOST, and the rise of Automotive Ethernet |
| [05 — Gateway ECU & Why CAN Won](./05_gateway_ecu_and_why_can_won.md) | How all networks connect via Gateway ECU, and the 5 reasons CAN dominates |

---

## Key Takeaway

A modern car has 50–150+ ECUs that cannot work in isolation. Pre-network vehicles ran kilometres of wire — heavy, expensive, and impossible to scale. Proprietary solutions from each OEM made things worse. This set the stage for **CAN bus** as the universal automotive networking standard.

A modern vehicle runs **multiple networks simultaneously**, each chosen for its job:
- **CAN** → the reliable backbone (powertrain, safety)
- **LIN** → cheap and slow (comfort, body)
- **FlexRay** → deterministic timing (x-by-wire)
- **MOST** → multimedia (being replaced)
- **Automotive Ethernet** → the fast future (ADAS, cameras, OTA)

The **Gateway ECU** is the translator sitting in the middle, bridging all these worlds together.

---

*Source: Personal handwritten notes — learning in progress 🚗*
