# Client Side Information Gathering

When performing a client-side attack, the success of the attack will domce down to the accurancy of the information you gather about your target(s) and the client-side software and configuration running on the target system(s).

In order for you to successfully exploit a client-side vulnerability, or misconfiguration, you must first know what client-side software is running on a target system(s).

This is where the client-side information gathering and fingerprinting comes into play.

## Client Side Info Gathering

Info gathering is broken into **two categories**: 

* **Passive Client Information Gathering**:

Passive client information gathering involves collecting data about target users, systems, or networks, without directly interacting with them. This approach aims to gather information passively from publicly available sources through techniques like *OSINT*

* **Active Client Information Gathering**:

Active information gathering involves interacting directly with target systems, applications, or users to gather data about their client-side configurations, vulnerabilites, or behaviors. This approach aims to gather information through direct interaction, such as **client/browser fingerprinting**, **banner grabbing**, and **social engineering**.

## Passive Information Gathering

### **Open Source Intelligence (OSINT)**
* Examples: searching social media platforms (e.g.: LinkedIn, Twitter (x)) for employee profiles, company information, or job postings. 
* browsing public forums or websites for discussions about the organization or its technologies
* tools: google dorks for advanced search queries, maltego for data visualization and link analysis, theHarvester for email harvesting

### **Search Engine Reconnaissance**

* examples: using advanced search queries on search engines like Google to discover publicly available information about target individuals, organizations, systems
* tools: google search operators, Shodan Search enginer, DuckDuckGo

## Active Client Information Gathering

## **Client Fingerprinting**

examples: engaging with target individuals or employees through phone calls, emails, or other communication channels to gather sensitive information, credentials, or access permissions

tools: Social Engineering toolkits like SET (Social-Engineer Toolkit), PhishMe, BeEF (Browser Exploitation Framework)

## **Information Gathering Techniques**

---

🔗 [Client Side Attack Introduction](./client-side-attacks.md)

🔙 [Homepage](https://gilbertpwns.github.io)