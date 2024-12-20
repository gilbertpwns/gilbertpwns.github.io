# Implement Load Balancing on Compute Engine

For these labs I've generally needed to append the ```-project``` flag as it's not set by default.

* Implement Load Balancing on Compute Engine
    + Create Virtual Machine
    + Compute Engine: Qwik Start - Windows
    + Getting Started with Cloud Shell and gcloud
    + Set Up Network and Application Load Balancing
    + Implement Load Balancing on Compute Engine: Challenge Lab



## Getting Started with Cloud Shell and gcloud

## Set Up Network and Application Load Balancers

Set Up Network & HTTP Load Balancers, GCP Essentials


## Useful/Standard Commands

### List Commands

> gcloud auth list

> gcloud config list project

> gcloud compute instances get-serial-port-output [instance] --zone=us-central1-c --project [project]

---

### Set Project

> gcloud config set project [project]

### Set Region

> gcloud config set compute/region us-east1

#### Default Zone

> gcloud config set compute/zone us-east1-b

---

### RDP Validation

> gcloud compute instances get-serial-port-output [instance]--zone=us-central1-c --project [project]

gcloud compute instances get-serial-port-output [instance]--zone=us-central1-c --project [project]


## Clipboard

--- 

gcloud config set compute/region us-east1 --project qwiklabs-gcp-01-25afd165c52c

gcloud config set compute/zone us-east1-b --project qwiklabs-gcp-01-25afd165c52c

```
  gcloud compute instances create www1 \
    --zone=us-east1-b \
    --tags=network-lb-tag \
    --machine-type=e2-small \
    --image-family=debian-11 \
    --image-project=debian-cloud \
    --metadata=startup-script='#!/bin/bash
      apt-get update
      apt-get install apache2 -y
      service apache2 restart
      echo "
<h3>Web Server: www1</h3>" | tee /var/www/html/index.html'
```

```
student_02_95229239f3e4@cloudshell:~$ gcloud compute instances create --project qwiklabs-gcp-01-25afd165c52c  www1 \
    --zone=us-east1-b \
    --tags=network-lb-tag \
    --machine-type=e2-small \
    --image-family=debian-11 \
    --image-project=debian-cloud \
    --metadata=startup-script='#!/bin/bash
      apt-get update
      apt-get install apache2 -y
      service apache2 restart
      echo "
<h3>Web Server: www1</h3>" | tee /var/www/html/index.html'
```

```
Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-01-25afd165c52c/zones/us-east1-b/instances/www1].

NAME: www1
ZONE: us-east1-b
MACHINE_TYPE: e2-small
PREEMPTIBLE: 
INTERNAL_IP: 10.142.0.2
EXTERNAL_IP: 34.75.47.25
STATUS: RUNNING
```

```
  gcloud compute instances create --project qwiklabs-gcp-01-25afd165c52c www2 \
    --zone=us-east1-b \
    --tags=network-lb-tag \
    --machine-type=e2-small \
    --image-family=debian-11 \
    --image-project=debian-cloud \
    --metadata=startup-script='#!/bin/bash
      apt-get update
      apt-get install apache2 -y
      service apache2 restart
      echo "
<h3>Web Server: www2</h3>" | tee /var/www/html/index.html'
```

```
  gcloud compute instances create --project qwiklabs-gcp-01-25afd165c52c www3 \
    --zone=us-east1-b  \
    --tags=network-lb-tag \
    --machine-type=e2-small \
    --image-family=debian-11 \
    --image-project=debian-cloud \
    --metadata=startup-script='#!/bin/bash
      apt-get update
      apt-get install apache2 -y
      service apache2 restart
      echo "
<h3>Web Server: www3</h3>" | tee /var/www/html/index.html'
```

#### Firewall Rule to Allow External Traffic to these VMs

> gcloud compute firewall-rules create --project qwiklabs-gcp-01-25afd165c52c www-firewall-network-lb \
    --target-tags network-lb-tag --allow tcp:80

#### Validate 

> gcloud compute instances list --project qwiklabs-gcp-01-25afd165c52c

```
student_02_95229239f3e4@cloudshell:~$ gcloud compute instances list --project qwiklabs-gcp-01-25afd165c52c
NAME: www1
ZONE: us-east1-b
MACHINE_TYPE: e2-small
PREEMPTIBLE: 
INTERNAL_IP: 10.142.0.2
EXTERNAL_IP: 34.75.47.25
STATUS: RUNNING

NAME: www2
ZONE: us-east1-b
MACHINE_TYPE: e2-small
PREEMPTIBLE: 
INTERNAL_IP: 10.142.0.3
EXTERNAL_IP: 34.23.16.121
STATUS: RUNNING

NAME: www3
ZONE: us-east1-b
MACHINE_TYPE: e2-small
PREEMPTIBLE: 
INTERNAL_IP: 10.142.0.4
EXTERNAL_IP: 35.231.163.239
STATUS: RUNNING
```

### Verify Running Instances with Curl

> curl http://[IP_ADDRESS]

```
student_02_95229239f3e4@cloudshell:~$ curl http://34.75.47.25

<h3>Web Server: www1</h3>
student_02_95229239f3e4@cloudshell:~$ curl http://34.23.16.121

<h3>Web Server: www2</h3>
student_02_95229239f3e4@cloudshell:~$  curl http://35.231.163.239

<h3>Web Server: www3</h3>
```

### Configure the Load Balancing Service

Create a static external IP address for your load balancer

> gcloud compute addresses create network-lb-ip-1 \
  --region us-east1

> gcloud compute http-health-checks create basic-check

### Add a legacy HTTP health check resource

> gcloud compute http-health-checks create basic-check

```
student_02_95229239f3e4@cloudshell:~ (qwiklabs-gcp-01-25afd165c52c)$ gcloud compute http-health-checks create basic-check
Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-01-25afd165c52c/global/httpHealthChecks/basic-check].
NAME: basic-check
HOST: 
PORT: 80
```

### Add a target pool check

```
 gcloud compute target-pools create www-pool \
  --region us-east1 --http-health-check basic-check
```

```
student_02_95229239f3e4@cloudshell:~ (qwiklabs-gcp-01-25afd165c52c)$ gcloud compute target-pools create www-pool \
  --region us-east1 --http-health-check basic-check
Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-01-25afd165c52c/regions/us-east1/targetPools/www-pool].
NAME: www-pool
REGION: us-east1
SESSION_AFFINITY: NONE
BACKUP: 
HEALTH_CHECKS: basic-check
```

#### Add instances to pool

```
student_02_95229239f3e4@cloudshell:~ (qwiklabs-gcp-01-25afd165c52c)$ gcloud compute target-pools add-instances www-pool \
    --instances www1,www2,www3
Updated [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-01-25afd165c52c/regions/us-east1/targetPools/www-pool].
```

#### Add Forwarding Rule

```
student_02_95229239f3e4@cloudshell:~ (qwiklabs-gcp-01-25afd165c52c)$ gcloud compute forwarding-rules create www-rule \
    --region  us-east1 \
    --ports 80 \
    --address network-lb-ip-1 \
    --target-pool www-pool

Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-01-25afd165c52c/regions/us-east1/forwardingRules/www-rule].
```

### Send Traffic to Instances

#### View External IP of the www-rule forwarding rule used by the load balancer

> gcloud compute forwarding-rules describe www-rule --region us-east1

```
student_02_95229239f3e4@cloudshell:~ (qwiklabs-gcp-01-25afd165c52c)$ gcloud compute forwarding-rules describe www-rule --region us-east1
IPAddress: 34.148.224.223
IPProtocol: TCP
creationTimestamp: '2024-12-20T12:24:41.081-08:00'
description: ''
fingerprint: VBh7Pj1xJ_k=
id: '6826583892834151526'
kind: compute#forwardingRule
labelFingerprint: 42WmSpB8rSM=
loadBalancingScheme: EXTERNAL
name: www-rule
networkTier: PREMIUM
portRange: 80-80
region: https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-01-25afd165c52c/regions/us-east1
selfLink: https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-01-25afd165c52c/regions/us-east1/forwardingRules/www-rule
target: https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-01-25afd165c52c/regions/us-east1/targetPools/www-pool
```

#### Access the external IP address

> IPADDRESS=$(gcloud compute forwarding-rules describe www-rule --region us-east1 --format="json" | jq -r .IPAddress)

##### Show the external IP address

> echo $IPADDRESS

#### Use curl to access the external IP

replace IP_ADDRESS with an external address matching the previous command

> while true; do curl -m1 $34.148.224.223; done

### Create an Application Load Balancer

Application Load Balancing is implemented on Google Front End (GFE). GFEs are distributed globally and operate together using Google's global network and control plane. You can configure URL rules to route some URLs to one set of instances and route other URLs to other instances.

Requests are always routed to the instance group that is closest to the user, if that group has enough capacity and is appropriate for the request. If the closest group does not have enough capacity, the request is sent to the closest group that does have capacity.

To set up a load balancer with a Compute Engine backend, your VMs need to be in an instance group. The managed instance group provides VMs running the backend servers of an external Application Load Balancer. For this lab, backends serve their own hostnames.

### Create Load Balancer Template

```
gcloud compute instance-templates create lb-backend-template \
   --region=us-east1 \
   --network=default \
   --subnet=default \
   --tags=allow-health-check \
   --machine-type=e2-medium \
   --image-family=debian-11 \
   --image-project=debian-cloud \
   --metadata=startup-script='#!/bin/bash
     apt-get update
     apt-get install apache2 -y
     a2ensite default-ssl
     a2enmod ssl
     vm_hostname="$(curl -H "Metadata-Flavor:Google" \

http://169.254.169.254/computeMetadata/v1/instance/name)"
     echo "Page served from: $vm_hostname" | \
     tee /var/www/html/index.html
     systemctl restart apache2'
```

[Managed instance groups (MIGs)](https://cloud.google.com/compute/docs/instance-groups) let you operate apps on multiple identical VMs. You can make your workloads scalable and highly available by taking advantage of automated MIG services, including: autoscaling, autohealing, regional (multiple zone) deployment, and automatic updating.

### Create MIG based on template

```
gcloud compute instance-groups managed create lb-backend-group \
   --template=lb-backend-template --size=2 --zone=us-east1-b
```

```
student_02_95229239f3e4@cloudshell:~ (qwiklabs-gcp-01-25afd165c52c)$ gcloud compute instance-groups managed create lb-backend-group \
   --template=lb-backend-template --size=2 --zone=us-east1-b
Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-01-25afd165c52c/zones/us-east1-b/instanceGroupManagers/lb-backend-group].
NAME: lb-backend-group
LOCATION: us-east1-b
SCOPE: zone
BASE_INSTANCE_NAME: lb-backend-group
SIZE: 0
TARGET_SIZE: 2
INSTANCE_TEMPLATE: lb-backend-template
AUTOSCALED: no
```

### Create the 'fw-allow-health-check' firewall rule

```
gcloud compute firewall-rules create fw-allow-health-check \
  --network=default \
  --action=allow \
  --direction=ingress \
  --source-ranges=130.211.0.0/22,35.191.0.0/16 \
  --target-tags=allow-health-check \
  --rules=tcp:80
```

```
student_02_95229239f3e4@cloudshell:~ (qwiklabs-gcp-01-25afd165c52c)$ gcloud compute firewall-rules create fw-allow-health-check \
  --network=default \
  --action=allow \
  --direction=ingress \
  --source-ranges=130.211.0.0/22,35.191.0.0/16 \
  --target-tags=allow-health-check \
  --rules=tcp:80
Creating firewall...working..Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-01-25afd165c52c/global/firewalls/fw-allow-health-check].                   
Creating firewall...done.                                                                                                                                                    
NAME: fw-allow-health-check
NETWORK: default
DIRECTION: INGRESS
PRIORITY: 1000
ALLOW: tcp:80
DENY: 
DISABLED: False
```

Now that the instances are up and running, set up a global static external IP address that your customers will use to reach your load balancer

```
gcloud compute addresses create lb-ipv4-1 \
  --ip-version=IPV4 \
  --global
```
Output

```
student_02_95229239f3e4@cloudshell:~ (qwiklabs-gcp-01-25afd165c52c)$ gcloud compute addresses create lb-ipv4-1 \
  --ip-version=IPV4 \
  --global
Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-01-25afd165c52c/global/addresses/lb-ipv4-1].
```

```
gcloud compute addresses describe lb-ipv4-1 \
  --format="get(address)" \
  --global
```

34.149.117.35

#### Create a health check for the load balancer

```
gcloud compute health-checks create http http-basic-check \
  --port 80
```

Google Cloud provides health checking mechanisms that determine whether backend instances respond properly to traffic. For more information, please refer to the [Creating health checks](https://cloud.google.com/load-balancing/docs/health-checks) documentation.

#### Create backend service

```
gcloud compute backend-services create web-backend-service \
  --protocol=HTTP \
  --port-name=http \
  --health-checks=http-basic-check \
  --global
```

#### Add instance group as the backend to the backend service

```
gcloud compute backend-services add-backend web-backend-service \
  --instance-group=lb-backend-group \
  --instance-group-zone=us-east1-b \
  --global
```

#### Create a [URL map](https://cloud.google.com/load-balancing/docs/url-map-concepts) to route the incoming request to the default backend service

```
gcloud compute url-maps create web-map-http \
    --default-service web-backend-service
```

#### Create a target HTTP proxy to route requests to your URL map

```
gcloud compute target-http-proxies create http-lb-proxy \
    --url-map web-map-http
```

### Create a global forwarding rule to route incoming requests to the proxy

```
gcloud compute forwarding-rules create http-content-rule \
   --address=lb-ipv4-1\
   --global \
   --target-http-proxy=http-lb-proxy \
   --ports=80
```

Congratulations, you've created an L7 Application Load Balancer

---

↩️ [BACK](../gcp.md)
