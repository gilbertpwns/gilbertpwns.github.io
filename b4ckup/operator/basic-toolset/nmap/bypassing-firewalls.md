# Firewall and IPS/IDS Evasion

Nmap gives us many different ways to bypass firewall rules and IDS/IPS. These methods include the fragmentation of packets, the use of decoys, and others.

## IDS vs. IPS

**IDS** scans the network for potential attacks, analyzes them, and reports any detected attacks.

**IPS** complements the IDS by taking specific defensive measures if a potential attack should have been detected.

An IPS is generally an inline firewall that will act as the perimeter defensive mechanism of a network.

## Determine a Firewall and Their Rules

The packets can either be **dropped** or **rejected**. The **dropped** packets are ignored, and no response is returned from the host. The **dropped** packets are ignored, and no response is returned from the host.

Some examples of errors can be:

* Net unreachable
* Net prohibited
* Host unreachable
* Host prohibited 
* Port unreachable 
* Proto unreachable 

### SYN-Scan

> sudo nmap 10.129.2.28 -p 21,22,25 -sS -Pn -n --disable-arp-ping --packet-trace

### ACK-Scan

> sudo nmap 10.129.2.28 -p 21,22,25 -sA -Pn -n --disable-arp-ping --packet-trace



---

↩️ [BACK](../../README.md)