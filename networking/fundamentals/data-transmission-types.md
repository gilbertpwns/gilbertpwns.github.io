# Data Transmission Types

## Data Types

* Unicast - one-to-one
* Broadcast - one-to-all
* Multicast - one-to-a-group

##

You'll see a lot of multicast in streaming and video. Typically you have to open up some kind of multicast application. Your NIC needs to *find* multicast tranmissions and initialize it's communications. Multicast has a special and unique MAC address.

> Multicast reserved: 01-00-5E-XX-XX-XX

You'll never see a multicast in the *source* address, you will only see them in a *destination* address.

By default if a router receives any broadcast or multicast packets, it will drop them immediately. The router has the ability to process it though, but generally will not. The router is always the edge of a broadcast domain.



---
