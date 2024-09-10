# Hardening Distributions

There are simple steps in order to better secure your workloads.

## Basics

### Secure SSH Access

* Change the Default Port: Change the default SSH port (22) to a less common one to reduce automated attacks. Edit ```/etc/ssh/sshd_config``` and set ```Port``` to a different number.
* Disable Root Login: Prevent direct root login by setting ```PermitRootLogin``` no in ```/etc/ssh/sshd_config```.
* Use Key-Based Authentication: Instead of passwords, use SSH keys for authentication. Disable password-based authentication by setting ```PasswordAuthentication``` no.
* Limit User Access: Restrict SSH access to specific users by configuring the ```AllowUsers``` or ```AllowGroups``` directive in ```/etc/ssh/sshd_config```.

### Strong Passwords and Authentication

* **Enforce strong passwords**: tools like ```pam_cracklib``` or ```libpam-pwquality```
* 2FA

### Secure Network Configurations

* Disable IPv6: If not needed, you can disable IPv6 to reduce attack vectors. Edit ```/etc/sysctl.conf``` and set:

```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```
* Configure Network Security: Use tools like ```fail2ban``` to protect against brute-force attacks.


---

↩️ [BACK](../README.md)
