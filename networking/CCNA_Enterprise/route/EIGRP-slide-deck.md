# EIGRP

## 1.2.1 EIGRP Topology Table, Messages & Update Process

* what is the EIGRP topology table?
* after forming an EIGRP neighbor relationship, neighbors exchange toplogy tables
* routers first must add subnets into the local topology table
* the EIGRP topology table keeps basic information about each unique prefix, including prefix, prefix length, metric information, and a few other details

### Seeding the Local Topology Table

* a router can add routes into its local topology table in two ways
    + prefixes of connected subnets that are matched using the network command
    + prefixes that are redistributed to EIGRP

### EIGRP messages

* to understand topology exchange, we need to konw that there are five types of protocol messages:
    + hello
    + update
    + ACK
    + query 
    + reply
* EIGRP uses Update and ACK messages for topology exchange
* update messages contain the following information:
    + prefix 
    + prefix length
    + metric components 

### EIGRP update process

* EIGRP uses Update and ACK messages for topology exchange
* update messages contain the following information:
    + prefix
    + prefix length
    + matric components: bandwidth, delay, load & reliability
    + nonmetric components: MTU and hop count

### EIGRP Update Process

* when neighbors come up, the routers exchange full topology tables each other
* when full topology table exchange is done, there NO periodic re-flooding of toplogy table data
* if something changes, only a partial update is sent about the prefix that was affected with a network change

* this change can be as small as a metric value change for a prefix, or it can be something like a link failure, etc.
* if a neighbor fails and then recovers, the full topology table is exchanged with it again.
* a full topology table is exchanged with any new neighbor/adjaceny formed
* by default, EIGRP implements split-horizon
* EIGRP uses RTP (reliable transport protocol) to send updates and ACK messages
* on multi-access EIGRP, typically send update messages to multicast address 224.0.0.10 and expect unicast EIGRP ACK message from each neighbor

## EIGRP Topology Exchange over WAN

### EIGRP Split Horizon Issue

* EIGRP by default, has split-horizon enabled on Frame Relay multipoint interfaces.
* With split horizon, an update received on a certain interface cannot go out the same interface
* Toplogy update problem:

* L2 topology doesn't match L3
* To disable split horizon on any interface, use the following command:

```
no ip split-horizon <asn> (interface-level command)
Rack1R1#sh ip int fa0/0
FastEthernet0/0 is up, line protocol is up
<omitted>
Split horizon is enabled (default behavior)
<omitted>
```

## EIGRP Percentage Bandwidth 

* On NMBA media, EIGRP updates cannot be sent because the underlying Layer 2 media does not support multicast packets
* Normally a single update sent to _224.0.0.10_
* In this case, EIGRP must send a copy of update message to each reachable neighor




---

🔙 [Homepage](../../README.md)

🔙 [Routing Table of Contents](./route.md)
