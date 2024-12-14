# Web Proxies

* What are web proxies?
* Getting starting with Burp Suite and ZAP
* Setting up our application testing environment
* Using Burp/ZAP to intercept and manipulate web requests
* Using Burp/ZAP to manipulate web responses and enable disable/hidden features
* Repeating web requests for quick testing
* Proxying web traffic from other tools through Burp
* Using built-in fuzzers to fuzz different endpoints and identify potential vulnerabilities
* Using Passive/Active scanners to discover web vulnerabilities
* Extending both tools with plugins and add-ons

## Intro to Web Proxies

Today, most modern web and mobile applications work by continuously connecting to back-end servers to send and receive data and then processing this data on the user's device, like their web browsers or mobile phones. Web proxies are specialized tools that can be set up between a browser/mobile application and a back-end server to capture and view all the web requests being sent between both ends, essentially acting as man-in-the-middle (MITM) tools.

Web proxies are considered among the most essential tools for any web pentester. They significantly simplify the process of capturing and replaying web requests compared to earlier CLI-based tools. Once a web proxy is set up, we can see all HTTP requests made by an application and all of the responses sent by the back-end server.

While the primary use of web proxies is to capture and replay HTTP requests, they have many other features that enable different uses for web proxies. The following list shows some of the other tasks we may use web proxies for:

* Web application vulnerability scanning
* Web fuzzing
* Web crawling
* Web application mapping
* Web request analysis
* Web configuration testing
* Code reviews

## Burp Suite

Burp Suite (Burp) -pronounced Burp Sweet- is the most common web proxy for web penetration testing. It has an excellent user interface for its various features and even provides a built-in Chromium browser to test web applications.

## OWASP Zed Attack Proxy (ZAP)

OWASP Zed Attack Proxy (ZAP) is another common web proxy tool for web penetration testing. ZAP is a free and open-source project initiated by the Open Web Application Security Project (OWASP) and maintained by the community, so it has no paid-only features as Burp does. 

---

↩️ [BACK](../../README.md)
