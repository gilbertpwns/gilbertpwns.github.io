# Logs and Logging

## Enable Logging

### dropped packets

sudo iptables -A INPUT -j LOG --log-prefix "IPTABLES DROP: " --log-level 4

### accepted packets

sudo iptables -A INPUT -j LOG --log-prefix "IPTABLES ACCEPT: " --log-level 6


## Check Logs

> sudo tail -f /var/log/syslog | grep "IPTABLES"
> sudo tail -f /var/log/messages | grep "IPTABLES"

---

↩️ [BACK](../README.md)