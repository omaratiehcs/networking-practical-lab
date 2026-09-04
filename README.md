# Networking Practical Lab

A practical enterprise networking lab built with Cisco Packet Tracer, documenting VLANs, inter-VLAN routing, DHCP, static routing, NAT/PAT, and network troubleshooting.

## Current Version

**V1 — Routed Enterprise Network**

This version represents the completed baseline topology. It is intentionally frozen; future substantial changes will be developed as V2, V3, and so on.

## Lab Goals

- Build and troubleshoot an enterprise-style routed network.
- Practice VLAN segmentation and 802.1Q trunking.
- Configure inter-VLAN routing on a Layer-3 switch using SVIs.
- Configure DHCP for internal VLANs.
- Configure routed Layer-3 links between the core and routers.
- Practice static routing and understand return paths.
- Build a simple branch network and connect it to headquarters.
- Verify end-to-end connectivity and understand traffic flow.
- Document the lab as a portfolio project.

## V1 Topology

```text
                         R-HQ
                           |
                     L3 CORE SWITCH
                    /      |       \
                   /       |        \
              SW-HR      SW-ENG    SW-SALES
                |           |          |
             HR PCs      ENG PCs     Sales PCs
                            |
                          Server

                         R-HQ
                           |
                         R-EDGE
                        /       \
                    R-ISP     R-BRANCH
                                |
                           SW-BRANCH
                          /    |    \
                        PC1   PC2   PC3
```

## V1 Technologies

- Cisco IOS switching and routing
- VLANs
- 802.1Q trunks
- Native VLAN
- SVIs
- Layer-3 routed switch ports
- Inter-VLAN routing
- DHCP
- IPv4 subnetting
- Static routing
- NAT/PAT concepts
- ICMP and ping-based verification
- Cisco show/debug-style verification workflow

## V1 Addressing Summary

| Network / Purpose | Subnet |
|---|---|
| Engineering VLAN 10 | 10.10.10.0/24 |
| HR VLAN 20 | 10.10.20.0/24 |
| Sales VLAN 30 | 10.10.30.0/24 |
| Servers VLAN 40 | 10.10.40.0/24 |
| Management VLAN 99 | 10.10.99.0/24 |
| Branch LAN | 10.20.10.0/24 |
| R-HQ ↔ R-EDGE | 10.255.0.0/30 |
| R-EDGE ↔ R-BRANCH | 10.255.0.4/30 |
| R-HQ ↔ Core | 10.255.0.8/30 |
| R-ISP ↔ R-EDGE | 203.0.113.0/30 |

## VLANs

| VLAN | Name | Purpose |
|---:|---|---|
| 10 | ENGINEERING | Engineering users |
| 20 | HR | HR users |
| 30 | SALES | Sales users |
| 40 | SERVERS | Internal server network |
| 99 | MANAGEMENT | Network management |
| 999 | NATIVE | Unused native VLAN for trunks |

## Key Design Decisions

- HQ uses a Layer-3 core switch for inter-VLAN routing.
- Access-switch uplinks are 802.1Q trunks.
- The Core ↔ R-HQ connection is a routed Layer-3 link, not a trunk.
- VLAN 999 is used as the native VLAN on HQ trunks.
- The branch remains a simple flat VLAN 1 LAN in V1 rather than adding unnecessary segmentation.
- Static routing is used in V1 to make routing behavior and return paths explicit.
- V1 is frozen as the baseline for future versions.

## Verification

V1 was verified at both infrastructure and host level. The final tests confirmed successful connectivity between branch hosts and HQ Engineering, HR, Sales, and Server networks.

Detailed verification evidence and device configurations are stored under `V1-Routed-Enterprise-Network/`.

## Versioning Workflow

**Build → Test → Document → Version → GitHub**

Each substantial topology or configuration change will become a new version instead of modifying the frozen V1 baseline.
