# PBR - Policy Based Routing

Difficulty: 🟨🟨🟨⬜⬜

Writing from my perspective and mostly in application to Cisco IOS/IOS-XE environments. These concepts will widely apply to other routing platforms amongst Cisco, and other companies (e.g. Catalyst, ISR, ASR, Juniper, Aruba, Palo-Alto, Arista)

## What is Policy-Based Routing

PBR allows a router or layer-3 switch to make forwarding decisions based on criteria other than the destination IP address.

A standard router follows this process:

1. receive packet
2. consult routing table
3. forward via best route

**With PBR**:

1. receive packet
2. evaluate policy
3. if policy matches, override routing table
4. forwarding according to policy
5. if no match, use normal routing table

You can think of a PBR as: "If traffic meets specific conditions, send it somewhere other than where the routing table would normally send it."

## Why Use PBR?

Common enterprise use cases:
|Scenario|Purpose|
|:-:|:-:|
|Internet breakout steering| send selected applications out specific ISP circuits|
|WAN optimization|Direct traffic to Silver Peak, Riverbed, etc.|
|Security Inspection|Force traffic through Firewalls or IDS|
|Vendor VPN Selection|Route partner traffic into specific tunnels|
|Saas optimization|Direct Microsoft 365 traffic through preferred path|
|Voice traffic preference|Force VoIP onto low-latency circuits|
|Migration projects|Temporarily redirect traffic during cutovers|

### Cisco Brief Implementation Commands


```
!
ip access-list extended USERS
 permit ip 10.10.10.0 0.0.0.255 any
!
route-map PBR permit 10
 match ip address USERS
 set ip next-hop 172.16.1.1
!
interface vlan 10
 ip policy route-map PBR
!
```

### Cisco Validation Commands

```
!
show ip policy
!
show route-map
!
show access-list
!
show ip cef
!
show track
!
show ip sla statistics
!
```

---


