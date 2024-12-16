# Raspberry Pi! 

## Pi Hole Notes

### Disk Space Issue 

Check Disk Usage

> df -h

Clear Unused Logs, You can clear old logs to free up space:

> sudo pihole flush

Remove Unused Packages, Clean up any unnecessary packages that might be consuming space:

```
sudo apt-get autoremove
sudo apt-get clean
```

Delete Old FTL Database Entries, If you have a lot of query data, you can truncate the database:

> sudo pihole -f

Check for Large Files: Identify any large files that may be taking up space:

? sudo du -ah / | sort -rh | head -n 20

Database Optimization: You can also optimize the database:

 >sudo pihole -g

After completing these steps, monitor the disk usage again with df -h to ensure that you have reclaimed sufficient space. If the issue persists, you may need to look into more significant storage solutions or investigate which specific directories are using the most space.

## Updating Pi-Hole

To update Pi-hole, you can follow these simple steps:

```bash
sudo apt update
sudo apt upgrade -y
```

Run the Pi-hole Update Script: Execute the Pi-hole update command:

> pihole -up

Check the version: 

> pihole -v

Restart Pi-hole (if necessary): Sometimes, it’s a good idea to restart the FTL service:

> sudo systemctl restart pihole-FTL


## Update OD on raspberri pi raspbian 10

```bash
sudo apt full-upgrade -y
sudo apt autoremove -y
```

---

↩️ [BACK](../README.md)
