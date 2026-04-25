# 03 — CAN & LIN: The Workhorses

> **Personal notes from my CAN learning journey** — transcribed from handwritten notes, Page 3

---

## 5 Major Vehicle Network Technologies

> Think of a vehicle's network like a city's transport system — you don't use a highway for a footpath, and you don't use a bicycle lane for cargo trucks.

Different jobs demand different networks. The 5 major ones are:

| Protocol | Speed | Primary Use |
|----------|-------|-------------|
| **CAN** | 125 Kbps – 1 Mbps | Powertrain, chassis, safety |
| **LIN** | 1 – 20 Kbps | Simple body functions |
| **FlexRay** | Up to 10 Mbps | Safety-critical real time |
| **MOST** | 25 – 150 Mbps | Multimedia |
| **Automotive Ethernet** | 100 Mbps – 10 Gbps | ADAS, cameras, OTA updates |

---

## CAN — Controller Area Network

**Speed:** 125 Kbps – 1 Mbps  
**Standard:** ISO 11898  
**Developed by:** Bosch, 1986

### Key Characteristics

- **The backbone** of vehicle networking — used in almost every car
- Handles: engine, brakes, transmission, airbags, steering
- **Multi-Master, Broadcast** — any node can transmit; all nodes hear it
- **Built-in error detection** — extremely reliable in harsh environments

---

## LIN — Local Interconnect Network

**Speed:** 1 – 20 Kbps  
**Primary use:** Simple body functions

### Key Characteristics

- Much simpler and cheaper than CAN
- **Single Master, Multiple Slaves** topology
- Used for: seat motors, mirror adjustments, door locks, window switches, rain sensors — things that **don't need to be fast**
- A LIN cluster is usually connected to the main CAN bus through a **Gateway ECU** (the central hub that handles efficient communication between various vehicle networks)

---

*Previous: [02 — Early Networks & Problems](../introduction/02_early_networks_and_problems.md)*  
*Next: [04 — FlexRay, MOST & Automotive Ethernet](./04_flexray_most_automotive_ethernet.md)*
