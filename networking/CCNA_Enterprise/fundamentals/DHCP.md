# DHCP - Dynamic Host Resolution Protocol

Difficulty: 🟩⬜⬜⬜⬜

## What is DHCP

**Dynamic Host Configuration Protocol (DHCP)** is a network service that automatically assigns:

* IP address
* Subnet Mask
* Default Gateway
* DNS Server
* Domain Name
* NTP Server
* Additional vendor-specific options

Without DHCP, every endpoint would require manual configuration.

---

## Why DHCP Matters

Imagine a corporate campus with:

* 5,000 PCs
* 1,500 Phones
* 2,000 Wireless Devices
* 400 Printers

Manual IP assignment would be impossible to manage.

DHCP provides:

✅ Centralized IP management

✅ Consistency

✅ Reduced configuration errors

✅ Faster endpoint deployment

✅ Better IP utilization

## DHCP Relay Agent

Forwards DHCP traffic between VLANs

```
!
ip helper-address
!
```

DHCP Discover messages are broadcasts. Broadcasts do NOT cross Layer-3 boundaries.

```
!
interface vlan 10
 ip helper-address 10.100.100.10
!
```

## Discover, Offer, Request, Acknowledge (DORA)

DORA is a quinessential that all Network Engineers should be aware of and understand.

### Cisco IOS DHCP Server Configuration

Small environments often use routers.

---

[]