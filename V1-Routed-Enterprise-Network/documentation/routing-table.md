# V1 Routing Design

V1 uses static routing. The purpose is to make the forwarding path and return-path requirement explicit while building the fundamentals needed before dynamic routing.

## R-HQ

Routes toward the HQ VLANs point to the Core at `10.255.0.10`:

```cisco
ip route 10.10.10.0 255.255.255.0 10.255.0.10
ip route 10.10.20.0 255.255.255.0 10.255.0.10
ip route 10.10.30.0 255.255.255.0 10.255.0.10
ip route 10.10.40.0 255.255.255.0 10.255.0.10
ip route 10.10.99.0 255.255.255.0 10.255.0.10
```

Additional routes:

```cisco
ip route 10.255.0.4 255.255.255.252 10.255.0.1
ip route 203.0.113.0 255.255.255.252 10.255.0.1
ip route 10.20.10.0 255.255.255.0 10.255.0.1
```

## Core

The Core has a default route toward R-HQ:

```cisco
ip route 0.0.0.0 0.0.0.0 10.255.0.9
```

Its VLAN networks are directly connected through SVIs.

## R-EDGE

```cisco
ip route 10.10.10.0 255.255.255.0 10.255.0.2
ip route 10.10.20.0 255.255.255.0 10.255.0.2
ip route 10.10.30.0 255.255.255.0 10.255.0.2
ip route 10.10.40.0 255.255.255.0 10.255.0.2
ip route 10.10.99.0 255.255.255.0 10.255.0.2
ip route 10.20.10.0 255.255.255.0 10.255.0.6
```

## R-BRANCH

```cisco
ip route 10.255.0.0 255.255.255.252 10.255.0.5
ip route 203.0.113.0 255.255.255.252 10.255.0.5
ip route 10.10.10.0 255.255.255.0 10.255.0.5
ip route 10.10.20.0 255.255.255.0 10.255.0.5
ip route 10.10.30.0 255.255.255.0 10.255.0.5
ip route 10.10.40.0 255.255.255.0 10.255.0.5
ip route 10.10.99.0 255.255.255.0 10.255.0.5
```

## Routing Principle Demonstrated

A route must exist in both directions for two-way communication. The branch-to-HQ troubleshooting exercise demonstrated this: the branch could reach its gateway, but end-to-end communication required routes through R-EDGE and R-HQ back toward the Branch LAN.
