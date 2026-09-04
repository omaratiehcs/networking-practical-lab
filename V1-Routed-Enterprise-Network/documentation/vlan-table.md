# V1 VLAN Table

| VLAN | Name | Purpose | HQ Access Switch Assignment |
|---:|---|---|---|
| 10 | ENGINEERING | Engineering users | SW-ENG |
| 20 | HR | HR users | SW-HR |
| 30 | SALES | Sales users | SW-SALES |
| 40 | SERVERS | Internal server network | Server connected through SW-ENG |
| 99 | MANAGEMENT | Network management | Reserved for management |
| 999 | NATIVE | Native VLAN on trunks | Trunk-only/native VLAN |

## Trunks

All HQ access-switch uplinks to the Core are configured as 802.1Q trunks.

### Core Fa0/1 ↔ SW-HR Fa0/4

- Mode: trunk
- Native VLAN: 999
- Allowed VLANs: 10,20,30,40,99,999

### Core Fa0/2 ↔ SW-ENG Fa0/2

- Mode: trunk
- Native VLAN: 999
- Allowed VLANs: 10,20,30,40,99,999

### Core Fa0/3 ↔ SW-SALES Fa0/1

- Mode: trunk
- Native VLAN: 999
- Allowed VLANs: 10,20,30,40,99,999

## Important Design Note

The Core Fa0/4 ↔ R-HQ G0/1 connection is a routed Layer-3 link. It is **not** a trunk and does not carry the HQ VLANs as an 802.1Q trunk.
