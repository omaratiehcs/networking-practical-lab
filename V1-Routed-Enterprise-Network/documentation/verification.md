# V1 Verification

## Infrastructure Verification

The following checks were completed during the V1 build:

- Core VLANs created and verified.
- HQ access-switch uplinks verified as trunks.
- Native VLAN 999 verified on HQ trunks.
- Allowed VLAN list verified on HQ trunks.
- Core SVIs for VLANs 10, 20, 30, 40, and 99 verified `up/up`.
- Core routing table verified with directly connected VLAN networks and the routed R-HQ link.
- DHCP pools and bindings verified for Engineering, HR, and Sales.
- Server in VLAN 40 configured with a static address and verified against its gateway.
- R-HQ, R-EDGE, and R-BRANCH routing tables verified.
- R-HQ ↔ Core link verified as a routed Layer-3 connection.
- Branch switch verified as a simple VLAN 1 access network.
- Final end-to-end connectivity tests succeeded.

## Host-Level Verification

The final tests confirmed successful communication between Branch hosts and:

- Engineering hosts
- HR hosts
- Sales hosts
- Server VLAN

Inter-VLAN communication inside HQ was also tested successfully.

## Troubleshooting Lessons

### Branch Reachability

A Branch PC could reach its local default gateway but initially could not reach an HQ host. The problem was not the Branch PC or local switch. The routing path lacked the necessary routes for the Branch LAN on the upstream routers.

After adding the Branch network route to R-EDGE and the corresponding return route to R-HQ, end-to-end connectivity succeeded.

This reinforced an important troubleshooting principle:

> Local gateway reachability does not prove end-to-end routing is correct.

### SW-BRANCH

The Branch switch intentionally remains a flat VLAN 1 switch in V1. No HQ VLANs were added because the Branch LAN is a separate routed network in this version.

## V1 Status

**PASS — baseline topology and configuration verified.**
