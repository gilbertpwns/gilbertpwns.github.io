# Automation with Python

## YANG (Yet Another Next Generation)

YANG is a data modeling language used to model the configuration and state data manipulated by network management protocols such as:

* NETCONF (Network Configuration Protocol)
* RESTCONF

YANG was originally defined in RFC 6020 and later updated in RFC 7950. It's structured hierarchical, and designed to describe:

* Network device configuration
* Operational state (read-only telemetry)
* Notification (event-driven alerts)

YANG is a blueprint or template for how network device should be configured and what kind of data it can share.

* Just like:
    - a form tells you what fields to fill in (name, age, or email)
    - YANG models tell the network system what configuration options exist (like intf., IP address, status), and how they should look.
* It doesn't do the configuration itself - only defines the structure.
* imagine a hotel registration form:
    - it tells you where to write your name, email, number of nights, etc.
    - you can't just write anything anywhere - the form has rules!
* YANG works the same way - it defines the 'form' that tools like NETCONF or RESTCONF use to send data to a router or switch

---
