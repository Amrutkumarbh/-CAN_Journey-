# 01 — What is Vehicle Networking?

> **Personal notes from my CAN learning journey** — transcribed from handwritten notes, Page 1

---

## The Problem: A Modern Car is a Computer on Wheels

A modern car has anywhere between **50 to 150+ Electronic Control Units (ECUs)** — small, dedicated computers each responsible for exactly one job.

### Common ECUs in a modern vehicle

| ECU | Full Name | Responsibility |
|-----|-----------|----------------|
| ECU / ECM | Engine Control Unit / Module | Fuel injection, ignition |
| TCM | Transmission Control Module | Gear shifting logic |
| ABS Module | Anti-lock Braking System | Braking control |
| ACU | Airbag Control Unit | Airbag deployment |
| BCM | Body Control Module | Windows, wipers, lights |
| — | Infotainment / Head Unit | Audio, navigation, display |
| ADAS Module | Advanced Driver Assistance System | Lane assist, adaptive cruise, parking sensor |
| BMS | Battery Management System | EV battery monitoring |
| TPMS, HVAC, Power Seats | ... | Many more |

---

## Why ECUs Can't Work in Isolation

> These ECUs don't work in isolation — they **constantly need to share data with each other**.

For example, the Engine RPM signal is needed by:
- Instrument Cluster (display to driver)
- TCM (for gear shifting decisions)
- ABS (traction control)
- ECM (engine management itself)

---

## What Happened Without a Network? (Pre-1980s)

Early cars used **point-to-point wiring** — every sensor and actuator was directly connected wherever it was needed.

**The consequence:** If Engine RPM needed to reach 4 different destinations (Cluster, TCM, ABS, ECM), you physically ran **4 separate wires**.

This approach quickly became unsustainable as cars grew smarter.

---

*Next: [02 — Why Vehicle Networks Were Needed + Early Solutions](./02_early_networks_and_problems.md)*
