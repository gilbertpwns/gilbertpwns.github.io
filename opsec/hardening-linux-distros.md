# Hardening Distributions

There are simple steps in order to better secure your workloads.

## Basics

### Secure SSH Access

* Change the Default Port: Change the default SSH port (22) to a less common one to reduce automated attacks. Edit ```/etc/ssh/sshd_config``` and set ```Port``` to a different number.
* Disable Root Login: Prevent direct root login by setting ```PermitRootLogin``` no in ```/etc/ssh/sshd_config```.
Use Key-Based Authentication: Instead of passwords, use SSH keys for authentication. Disable password-based authentication by setting ```PasswordAuthentication``` no.
Limit User Access: Restrict SSH access to specific users by configuring the ```AllowUsers``` or ```AllowGroups``` directive in ```/etc/ssh/sshd_config```.
---

↩️ [BACK](../README.md)
