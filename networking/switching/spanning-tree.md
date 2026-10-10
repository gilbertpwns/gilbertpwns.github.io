# Spanning-Tree Protocol

## Changes v. Classic STP

| Item | Classic | RSTP |
|:-:|:-:|:-:|
| States | Blocking, Listening, Learning Forwarding | Discarding, Learning, Forwarding | 
| Roles | Root, Designated, Blocking | Root, Designated, Alternate, Backup |
| Convergence | Timers (forward delay, ,max age) | Handshake on full-duplex links; timers are fallback | 
| Edge Ports | PortFast (Cisco) | Edge port goes forwarding immediately | 
| Link Type | Not explicit | Point-to-point (full duplex) required for rapid transition | 


## Bridging Loops and Loop Prevention

* What is a bridging loop
* Intro to Rapid Spanning Tree
* The Concept of Trees as related to RSTP

Traffic that needs to be flooded by switches. If a switch doesn't find a particular MAC in it's MAC address table, it will flood it.





---

🔙 [Homepage](../../README.md)
