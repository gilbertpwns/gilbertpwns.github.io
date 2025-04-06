# Host Discovery

- [ ] Enumeration
- [ ] Nmap
- [ ] Host Discovery
- [ ] Host and Port Scanning
- [ ] Saving Results
- [ ] Service Enumerations

## Bypassing Security Measures

- [ ]  Firewall and IDS/IPS Evation


You can only understand results if we know what they mean and how they're obtained. With that said, let's kick it off. This is what you need:

* Open ports and its services 
* Service version
* Info that the services providde. 
* Operating System

There are six differnt states

* *open* - this indicates that the connection to the scanned ports has been established. These connections can be **TCP** connections, **UDP** datagrams as well as **SCTP** associations.
* *closed*  when a port is shown as closed, the TCP protocol indicates that the packet we recieved back contains contains an **RST** flag. This scanning method can also be used to determine i four target is alive or not.
* *filtered* - Nmap cannot correctly identify whether the scanned port is open or closed because either no respose is returneed from the target from the target port or we get an error code rom the target. 
* *unfiltered* - This state of a port only occurs during tnhe **TCP-ACK** scan an means that the port is accessible,
* *open\|filtered* - if we di bit get a resonse for a specific port, **nnmap** will set it to that state, This indicates that the firewall or packet filter may protect the port
* *closed\|filtered* - This state only occurs in the **IP ID idle** scans and indicates that it was impossible to determine if the scanned port is closed or filtered by the Firewall

## Discovering Open TCP Ports

By default, **Nmap** scans the top 1000 TCP ports with the SYN scan (-sS). This SYN scan is set only to default when we run it as root because of the socket permissions required to create raw TCP packets. Otherwise, the TCP scan (-sT) is performed by default. This means that if we do not define ports and scanning methods, these paramters are set automatically.

We can define the ports one by one ```-p 22,25,80,139,445```, by range ```-p 22-445```, by top ports ```--top-ports=10``` from the Nmap database that have been signed as most frequent, by scanning all ports ```-p-``` but also by defining a fast port scan, which contains top 100 ports ```-F```.

### Working examples

> sudo nmap 10.129.2.28 --top-ports=10 

If we trace the packets Nmap sends, we will see the RST flag on TCP port 21 that our target sends back to us. To have a clear view of the SYN scan, we disable the ICMP echo requests (-Pn), DNS resolution (-n), and ARP ping scan (--disable-arp-ping).

> sudo nmap 10.129.2.28 -p 21 --packet-trace -Pn -n --disable-arp-ping

The Nmap TCP Connect Scan (-sT) uses the TCP three-way handshake to determine if a specific port on a target host is open or closed. The scan sends an SYN packet to the target port and waits for a response. It is considered open if the target port responds with an SYN-ACK packet and closed if it responds with an **RST** packet.

The **Connect** scan (also known as a full TCP connect scan) is highly accurate because it completes the three-way TCP handshake, allowing us to determine the exact state of a port (open, closed, or filtered). However, it is not the most stealthy. In fact, the Connect scan is one of the least stealthy techniques, as it fully establishes a connection, which creates logs on most systems and is easily detected by modern IDS/IPS solutions.

It is also useful when the target host has a personal firewall that drops incoming packets but allows outgoing packets. In this case, a Connect scan can bypass the firewall and accurately determine the state of the target ports. However, it is important to note that the Connect scan is slower than other types of scans because it requires the scanner to wait for a response from the target after each packet it sends, which could take some time if the target is busy or unresponsive.

Scans like the SYN scan (also known as a half-open scan) are generally considered more stealthy because they do not complete the full handshake, leaving the connection incomplete after sending the initial SYN packet. This minimizes the chance of triggering connection logs while still gathering port state information. Advanced IDS/IPS systems, however, have adapted to detect even these subtler techniques.

> sudo nmap 10.129.2.28 -p 443 --packet-trace --disable-arp-ping -Pn -n --reason -sT 


---

↩️ [BACK](../../README.md)

