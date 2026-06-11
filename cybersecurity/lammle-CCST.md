# CCST Cisco® Certified - Support Technician

This study guide assumes you have experience in IT.

## Study Guide - Cybersecurity Exam

### Chapter 1 - Security Concepts

Essential Security Principles

1.1. Define essential security princples

    Vulnerabilities, threats, exploits, and risks; attack vectors; hardening; defense-in-depth; confidentiality, integrity, availability (CIA triangle); types of attackers; reasons for attacks; code of ethics

1.2. Explain common threats and vulnerabilities

Malware, ransomeware, denial of service, botnets, social engineering attacks (tailgating, spear phishing, phishing, vishing, smishing etc.), physical attacks, man in the middle, IoT vulnerabilities, insider threats, APTs

#### **Technology Based Attacks**

* Denial of Service (DoS)/Distributed Denial of Service (DDoS)
    - Mostly a thing of the past, not truly respected among security professionals as simplicity and it's ease to deploy
* The Ping of Death
    - Ping is primarily used to see whether a computer is responding to IP requests. 
    - A typical ping to a remote host consists of sending four normal-sized ICMP packets to a remote host to see whether it's available.
    - For a ping-of-death attack, a humongous ICMP packet is sent to the remote host victim, totally flooding the victim's buffer and causing the system to reboot, or helplesssly hang there, drowning. It's good to know what patches are available for most operating systems to prevent a ping-of-death attack from working.
* Distributed Denial of Service (DDoS)
    - Denial of Service attacks can be made more effective if they can be amplified by recruiting helpers in the attack process. Following this section is a number of effective methods explained.

### Botnet/Command and Control

    A botnet is a group of programs connected to the Internet for the purpose of performing a task in a coordinated manner.
    Some botnets, such as those created to maintain control of IRC channels, are legal, where others are illegaly created to leverage a DDoS.


#### Steps in building a botnet

---
