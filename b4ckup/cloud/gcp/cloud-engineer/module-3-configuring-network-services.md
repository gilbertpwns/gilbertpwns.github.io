# Configuring Network Services

## Scope

Explore the scope of tasks involved in configuring network services for Cymbal, which corresponds to the third section of the Professional Cloud Network Cloud Engineer Exam Guide.

##

* 3.1 Configuring Load Balancing
* 3.2 Configuring Google Cloud Armor Policies
* 3.3 Configuring Cloud CDN
* 3.4 Configuring and maintaining Cloud DNS
* 3.5 Configuring Cloud NAT
* 3.6 Configuring network packet inspection

## Quick Facts

You use Google Cloud DNS to map Cymbal Bank's domain names to the load balancer IP addresses.

You also protect compute resources from the internet by ensuring that they only have private internal IP addresses, and by setting firewall rules to allow access only from the load balancers.

### Cymbals external HTTPs load balancer with backend buckets

* Global external HTTP(s) load balancers can server both protocols with HTTP and HTTPS target proxies and URL maps
* Backend buckets are used to server static resources
* Backend services are used to serve dynamic resources

### Additional Load Balancing Scenarios

* Internal regional HTTP(s) or TCP/UDP load balancers for internal N-tier services or microservices
* External TCP/SSL proxy load balancers for global 

### Cloud CDN

* Cache Static resources at Google Cloud edge locations
* Easily Integrate with HTTP(s) load balancer
* Configure cache keys and TTL and optional cache invalidation
* Cache on-premises or other external origins
* Use signed URLs and cookies for authorized anonymous access 

### Configuring DNS

* map external IP addresses to registered domains
* managed private DNS for internal communications with Google Cloud resources
* Support multi-VPC, hybrid, and split-horizon configurations with peering and forwarding zones and inbound and outbound DNS server policies

### Configuring Cloud NAT

* providing secure requests to internet and responses back for private VMs with internal IP addresses only
* Automatice or configurable NAT sourrce IP address range
* Static or dynamic port allocation
* Configurable port re-use timeouts
* Applied to VMs using primary or alias internal IP addresses within specific subnets

### Configuring network packet inspection

* VMs with multiple network interfaces (multi-NIC) to connect trusted and untrusted networks
* Can run software to scan and filter traffic
* Packet mirroring to forward ingress and/or egress traffic from VMs to other VMs

### Diagnostic Questions

---

↩️ [BACK](../gcp.md)
