# Changelog

## V1 — Routed Enterprise Network

**Status:** Frozen baseline

### Added

- Enterprise-style HQ and branch topology in Cisco Packet Tracer.
- HQ VLAN segmentation:
  - VLAN 10 ENGINEERING
  - VLAN 20 HR
  - VLAN 30 SALES
  - VLAN 40 SERVERS
  - VLAN 99 MANAGEMENT
  - VLAN 999 NATIVE
- 802.1Q trunking between the HQ Core and access switches.
- Native VLAN 999 on HQ trunks.
- Layer-3 SVIs on the Core for inter-VLAN routing.
- DHCP pools for Engineering, HR, and Sales.
- Static server addressing in VLAN 40.
- Routed Layer-3 Core ↔ R-HQ connection.
- Static routing across R-HQ, R-EDGE, and R-BRANCH.
- Separate flat Branch LAN in VLAN 1.
- End-to-end connectivity verification.

### Key Troubleshooting Milestone

Branch hosts initially reached their local gateway but could not reach HQ networks. Static routes for the Branch LAN and the corresponding return path were added, after which end-to-end communication succeeded.

### Version Policy

V1 is intentionally frozen. Future substantial topology, addressing, routing, VLAN, security, or services changes will be implemented as a new version (V2, V3, etc.) rather than altering the V1 baseline.
