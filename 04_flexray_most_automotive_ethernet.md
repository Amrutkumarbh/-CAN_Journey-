# 04 — FlexRay, MOST & Automotive Ethernet

> **Personal notes from my CAN learning journey** — transcribed from handwritten notes, Page 4

---

## FlexRay

**Speed:** Up to 10 Mbps  
**Primary use:** Safety-critical real-time (steer-by-wire)

### Key Characteristics

- Designed for **safety-critical, time-deterministic** communication
- Used in **x-by-wire systems**: brake-by-wire, steer-by-wire, active suspension
- Has a **guaranteed time slot for each message** → no collision possible
- More complex and expensive than CAN → not used everywhere

---

## MOST — Media Oriented Systems Transport

**Speed:** 25 – 150 Mbps  
**Primary use:** Multimedia

### Key Characteristics

- Designed specifically for **multimedia** data
- Often uses **optical fiber** (ring topology)
- Found in infotainment systems, but being **replaced by Automotive Ethernet**

---

## Automotive Ethernet

**Speed:** 100 Mbps – 10 Gbps  
**Primary use:** ADAS, cameras, OTA updates

### Key Characteristics

- The **newest and fastest** — adapted from standard Ethernet for harsh automotive environments
- Used for: cameras, radar data, LiDAR, ADAS ECUs, OTA software updates
- Uses **single pair** (instead of 4-pair) — saves weight and space
- Rapidly taking over from MOST in high-bandwidth applications

---

## Quick Comparison Table

| Protocol | Speed | Topology | Best For | Cost |
|----------|-------|----------|----------|------|
| CAN | 125K – 1 Mbps | Multi-master bus | Powertrain, safety | Low |
| LIN | 1 – 20 Kbps | Single master / slave | Body comfort | Very Low |
| FlexRay | Up to 10 Mbps | Time-triggered | Steer/brake-by-wire | High |
| MOST | 25 – 150 Mbps | Ring (optical fiber) | Multimedia | High |
| Auto. Ethernet | 100M – 10 Gbps | Point-to-point | ADAS, cameras, OTA | Medium |

---

*Previous: [03 — CAN & LIN](./03_can_and_lin.md)*  
*Next: [05 — Gateway ECU & Why CAN Won](./05_gateway_ecu_and_why_can_won.md)*
