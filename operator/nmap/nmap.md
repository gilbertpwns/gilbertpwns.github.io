## Host Discovery

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

---

---

↩️ [BACK](./README.md)

