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

## Why use YANG?

* Let's say you want to automate configuration of 100 routers to: 
    - enable interfaces
    - set IP addresses
    - turn on routing protocols
* you don't want to do this manually in CLI for every device. You want a program to do it automatically and correctly
* here's where YANG helps:
    - it tells your script what settings are allowed (e.g, 'interface must have a name and IP address')
    - it ensures that all vendors follow the same structure (if they follow OpenConfig or IETF standards)
    * It prevents you from sending wrong or incomplete data

YANG can be written as follows:

```
interface:
    - name (required)
    - enabled (true/false)
    - IP address
```

then your automation tool uses this model to send:

```
{
    "interface":{
        "name": "GigabitEthernet0/0",
        "enabled": true,
        "ip": "192.168.1.1"
    }

}
```  

Imagine you're a network engineer responsible for configuring *hundred of routers* across different locations. Here's how *YANG*, *NETCONF*, *YANG Suite*, and *Python* fit into the picture.

### YANG = The Blueprint (Configuration Manual)

* YANG defines what can be configured on a router and how the data should look.
* think of it like the blueprint or config schema
* example: YANG defines that arouter interface has:
    - a name (string),
    - an IP address (IPv4 format),
    - an admin state (up/state).
* without YANG, devices might interpret config inconsistently

### NETCONF = The Delivery Truck with Rules

* NETCONF is a secure protocol used to deliver configurations to routers and retrieve operational data
* It uses XML payloads, which must match the **YANG-defined model**
* Think of NETCONF as a truck that delivers pre-packaged configuration
* You can't hand-write configs randomly - the truck (NETCONF) won't deliver malformed or invalid ones.

### YANG Suite = The Lab/Testing Branch

* YANG suite is a GUI tool provided by Cisco that helps you
    - Visualize YANG models
    - Generate and validate NETCONF payloads
    - Test and experiment with your configs before pushing them live.
* It's like a lab bench where you can safely prototype configurations, try out new schema changes, and troubleshoot.

### Python = The Automation Robot

* Here's where it scales
    - Python acts as the robotic automation system:
        + Read device inventory from a file or database
        + Pulls existing configuration using NETCONF
        + Builds new configuration using the YANG model structure
        + Sends the configuration using NETCONF client (like ncclient)
        + Logs success/failures, retries, and errors
    = Without Python, you'd be copying/pasting NETCONF XMLs manualy for each router - error-prone and inefficient

### Conclusion

* **YANG** is like a form template for network devices - it tells your tools what can be configure, how it should look, and helps automate it safely.


---
