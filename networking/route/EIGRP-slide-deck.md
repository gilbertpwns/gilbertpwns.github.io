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


---

🔙 [Homepage](../../README.md)

🔙 [Routing Table of Contents](./route.md)
