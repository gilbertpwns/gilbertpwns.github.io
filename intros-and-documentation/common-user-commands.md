# Common Commands

## DEBIAN COMMANDS

> lsb_release -a

## common

> sudo adduser grs

> sudo usermod -aG sudo grs

> sudo passwd grs

### make admin

```
sudo usermod -aG sudo username
groups username
su - username
sudo echo "I have sudo access!"
```

## LINUX PACKAGES


### ssh

```
sudo apt install openssh-server
sudo systemctl start ssh
sudo systemctl enable ssh
sudo systemctl status ssh
sudo ufw allow ssh
sudo ufw status
ip a
```

### installing xrdp

This installs the package, enables, and permits the firewall port.

```
sudo apt install xrdp
sudo systemctl start xrdp
sudo systemctl enable xrdp
sudo ufw allow 3389/tcp
sudo apt install xfce4
sudo systemctl restart xrdp
```

---

↩️ [BACK](../README.md)
