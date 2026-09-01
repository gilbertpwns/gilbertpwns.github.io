# Python - Device-Level Network Automation

## Constructing Network Automation

* Constructing a Network Automation Solution with Python & Netmiko
* Understanding Ncclient
* Constructing a Network Automation Solution with Python & Ncclient
* Constructing a Network Automation Solution with Python & RESTCONF
* Ansible Basics
* Constructing a Network Automation Solution with Ansible
* Constructing a Network Automation Solution for Day-0 Provisioning
* Construct On-Box Automations

## Understanding Netmiko

* **Netmiko** is an open-source Python library built on top of Paramiko (Python SSH Library)
* It was created by Kirk Byers to simplify the process of managing and automating network device through SSH
* While Paramiko provides general SSH capabilities, Netmiko adds network device-specific intelligence, making it far easier to interact with routers, switches, and firewalls from vendors like Cisco, Juniper, Arista, HP, and many more.
* Managing network devices involves tasks like:
    + logging in via SSH
    + sending configurations or show commands
    + parsing output
    + automating repetitive tasks
* Doing this directly with Paramiko requires a lot of low-level handling (prompt detection, delays, error handling). Netmiko abstracts that complexity by:
    + Handling device prompts automatically
    + managing command delays
    + supporting multiple device types/vendors
    + providing methods to send commands, configurations, and file transfers


* SSH Connection Handling: simplifies connecting to devices via SSH
* send_command(): executes show or exec-level commands 
* send_config_set(): Sends configuration commands in global config mode.
* send_config_from_file(): Pushes configurations stored in a file.
* File Transfers: Using scp_handler for uploading/downloading files.
* Error Handling: Built-in exception handling for authentication, timeouts, and command execution errors.
* Session Management: Context managers (with statement) for clean connections.

### import and define device details

```
from netmiko import ConnectHandler

cisco_device = {
    'device_type': 'cisco_ios'
    'ip': '192.168.1.1'
    'username': 'admin'
    'password': 'cisco123'
}
```

### establish connection:

```
connection = ConnectHandler(**cisco_device)
```

### send a command

```
output = connection.send_command("show ip interface brief")
print(output)
```

### send configuration

```
config_commands = [
    'interface g0/1',
    'description Connected_to_Server',
    'no shutdown'
]
connection.send_config_set(config_command)
```

###. Close

```
connection.disconnect()
```

---

🔙 [Homepage](../../README.md)