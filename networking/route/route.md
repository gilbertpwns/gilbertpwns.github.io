# Routing

## Contents


* [BGP](./#)
* [EIGRP](./EIGRP-slide-deck.md)
* [IPv6 Routing](./#)
* [OSPF](./#)
* [PBR](./#)
* [Redistribution](./#)

## Review of Routing

* reivew how routing table entries are learned
* review IPv6 and IPv4 routing tables
* distinguish local delivery from packet forwarding
* understand the purpose of IPv6 unicast routing
* enable IPv6 packet forwarding with IPv6 unicast-routing

## A Review of Routing Entries

* Routing table entries can be populated in one of three ways:
    + connected/local routes
    + dynamic routes (EIGRP, OSPF, RIP, etc.)
    + static routes

* routers contain routing tables for each type of layer-3 protocol they will be required to forward
    + IPv4 routing tables ("show ip route") 
    + IPv6 routing tables ("show ipv6 route")
* IPv4 routing tables are enabled by default 
* IPv6 routing tables may display entries, but additional commands may be neccesary to enable IPv6 packet forwarding

## Local Delivery vs Packet Forwarding



Routing protocols are comprised of 3 categories, link-state, distance vector, and advanced distance vectory (hybrid)

RIP is a distance vector protocol.

---

🔙 [Homepage](../../README.md)