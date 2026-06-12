# CCST Cisco® Certified - Support Technician

This study guide assumes you have experience in IT.

## Study Guide - Cybersecurity Exam

### Chapter 1 - Security Concepts

Essential Security Principles

**1.1. Define essential security princples**

Vulnerabilities, threats, exploits, and risks; attack vectors; hardening; defense-in-depth; confidentiality, integrity, availability (CIA triangle); types of attackers; reasons for attacks; code of ethics

**1.2. Explain common threats and vulnerabilities**

Malware, ransomeware, denial of service, botnets, social engineering attacks (tailgating, spear phishing, phishing, vishing, smishing etc.), physical attacks, man in the middle, IoT vulnerabilities, insider threats, APTs

#### **Technology Based Attacks**

* **Denial of Service (DoS)/Distributed Denial of Service (DDoS)**
    - Mostly a thing of the past, not truly respected among security professionals as simplicity and it's ease to deploy
* **The Ping of Death**
    - Ping is primarily used to see whether a computer is responding to IP requests. 
    - A typical ping to a remote host consists of sending four normal-sized ICMP packets to a remote host to see whether it's available.
    - For a ping-of-death attack, a humongous ICMP packet is sent to the remote host victim, totally flooding the victim's buffer and causing the system to reboot, or helplesssly hang there, drowning. It's good to know what patches are available for most operating systems to prevent a ping-of-death attack from working.
* **Distributed Denial of Service (DDoS)**
    - Denial of Service attacks can be made more effective if they can be amplified by recruiting helpers in the attack process. Following this section is a number of effective methods explained.

### Botnet/Command and Control

A botnet is a group of programs connected to the Internet for the purpose of performing a task in a coordinated manner. Some botnets, such as those created to maintain control of IRC channels, are legal, where others are illegaly created to leverage a DDoS.

#### Steps in building a botnet

1. botnet operator sends out viruses or worms whose payloads are malicious applications, the bots, infecting ordinary users' computers.
2. the bots on the infects PC log into a C&C server
3. at the right time, attacker, through C&C sends commands to all bots to attack the victim at the same time, thereby significantly amplifying the effect of the attack

### Traffic Spike

One of the hallmarks of a DDoS attack is a major spike in traffic in the network as bots that have been recruited mount the attack. For this reason, any major spike in traffic should truly be investigated.

A network IDS can recognize these traffic spikes and may be able to prevent them from growing larger or in some cases prevent the traffic from starting.

Smaller orgs


### Coordinated Attack

An unmistakable feature of a DDoS attack in the presence of a coordinated attack. If all bots can be instructed to attack precisely the same timing, the attack becomes much more overwhelming. Timing is key.

### Friendly/Unintentional DoS

Unintentional DoS attacks (friendly fire) are caused not by malicious actors, but it's a spike in activity to a website or resource that overpowers it's ability to respond.

In many cases it's a relatively unknown URL suddenly shared  in a larger medium such as a popular TV or news show. For example, when a particular celebrity died, Twitter and Google's traffic spiked so severly that at first it was interpreted as an automated attack.

### Physical Attack

Physical attacks exist and can be conducted against hardware devices. A damaged device is a bad device but these attacks can be mostly mitigated by preventing all types of unauthorized physical access. 

### Permanent DoS

A permanent DoS (PDoS) attack is one in which the device is damage and must be replaced. You may think it requires physical access to the device, but it doesn't necessarily. An attack called phlashing attacks the firmware located in systems. Using a fuzzer (introduce errors into) the firmware cause the device to be unusable.

Another approach is to introduce firmware images containing a Trojan or other types of malware.

### Smurfing

A version of DoS attacks that floods it's victims with spoofed broadcast ping messages. More on spoofing later, for now, understand that it basically steals someone else's IP address.

**how it works:** bad guy spoofs the intended victim's IP address and then sends many pings (IP echoes) to IP broadcast address (final IP address in a given subnet). The receiving router responds by delivering the broadcast to all hosts in the subnet, and all the hosts respond with an IP echo reply -- all of them at the same time. 

On a network with hundreds of hosts, this results in major network gridlock because all the machines are kepy busy responding to each echo request. The situation is even worse if the routers have not been configured to keep these types of broadcasts confined to the local subnet (unlikely) 



### SYN Flood

### Reflective/Amplified Attack

---

## DNS
## NTP
## DNS Poisoning
## VLAN Hopping
## ARP Spoofing
## Rogue DHCP
## IOT Vulnerabilities
## Rogue Access Point (AP)
## Evil Twin
## RandsomeWare

---

## Brute-Force
## Dictionary

## APT

## Hardening Techniques

---
