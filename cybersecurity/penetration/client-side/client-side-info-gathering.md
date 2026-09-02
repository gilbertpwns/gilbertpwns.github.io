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

## Social Engineering

examples: engaging with target individuals or employees through phone calls, emails, or other communication channels to gather sensitive information, credentials, or access permissions

tools: tools: Social Engineering toolkits like SET (Social-Engineer Toolkit), PhishMe, BeEF (Browser Exploitation Framework)

## More on Fingerprinting

Client fingerprinting is an active client information gathering technique used to gather information about a target system's web browser and underlying operating system in order to aid in the development of tailor made (client specific) payloads for initial access

* involves utilizing social engineering techniques like Phishing to coerce the target employee into clicking a link to a web page that we control
* this web server typically is configured to run a script that obtains information like broswer version and OS version from the browsers of users who visit the site
* JavaScript can be embedded into the homepage of the website and should log/send the browser fingerprint of users who visit the web page
* client-side informationg gathering technique needs the target's browser to be able to run the typical client-side code used in modern web pages (i.e: JavaScript)
* some privacy-focused browsers have the ability to block the execution of JavaScript code unless specified otherwise (this sounds simple or obvious, but is critical)

* primary objective is to identify the following:
    + web browser
    + web browser version
    + plugins/extensions
    + underlying OS information (OS, OS Version, System Architecture, etc.)
* browser fingerprinting webpage can leverage existing JS libraries like *fingerprintjs2*
    + [fingerprintjs2](https://github.com/LukasDrgon/fingerprintjs2)



---

🔗 [Client Side Attack Introduction](./client-side-attacks.md)

🔗 [Social Engineering](./social-engineering.md)

🔙 [Homepage](https://gilbertpwns.github.io)