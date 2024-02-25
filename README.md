# gilbertpwns.github.io

* [opsec](./opsec.md)

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

### xrdp

```
sudo apt install xrdp
sudo systemctl start xrdp
sudo systemctl enable xrdp
sudo ufw allow 3389/tcp
sudo apt install xfce4
sudo systemctl restart xrdp
```



---
