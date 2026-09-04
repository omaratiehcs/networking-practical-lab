# V1 Addressing Table

## LAN Networks

| Segment | VLAN | Network | Gateway |
|---|---:|---|---|
| Engineering | 10 | 10.10.10.0/24 | 10.10.10.1 |
| HR | 20 | 10.10.20.0/24 | 10.10.20.1 |
| Sales | 30 | 10.10.30.0/24 | 10.10.30.1 |
| Servers | 40 | 10.10.40.0/24 | 10.10.40.1 |
| Management | 99 | 10.10.99.0/24 | 10.10.99.1 |
| Branch LAN | 1 | 10.20.10.0/24 | 10.20.10.1 |

## Routed Links

| Link | Network | Side A | Side B |
|---|---|---|---|
| R-ISP ↔ R-EDGE | 203.0.113.0/30 | R-ISP: 203.0.113.1 | R-EDGE: 203.0.113.2 |
| R-EDGE ↔ R-HQ | 10.255.0.0/30 | R-EDGE: 10.255.0.1 | R-HQ: 10.255.0.2 |
| R-EDGE ↔ R-BRANCH | 10.255.0.4/30 | R-EDGE: 10.255.0.5 | R-BRANCH: 10.255.0.6 |
| R-HQ ↔ Core | 10.255.0.8/30 | R-HQ G0/1: 10.255.0.9 | Core Fa0/4: 10.255.0.10 |

## Host Addressing

### DHCP Hosts

- Engineering PC1: `10.10.10.2`
- Engineering PC2: `10.10.10.3`
- HR PC1: `10.10.20.2`
- Sales PC1: `10.10.30.2`

### Static Hosts

- Engineering server: `10.10.40.10/24`, gateway `10.10.40.1`, DNS `8.8.8.8`
- Branch PC1: `10.20.10.10/24`, gateway `10.20.10.1`, DNS `8.8.8.8`
- Branch PC2: `10.20.10.11/24`, gateway `10.20.10.1`, DNS `8.8.8.8`

> Branch PC3 exists in the topology; its final address was not documented in the V1 build notes.
