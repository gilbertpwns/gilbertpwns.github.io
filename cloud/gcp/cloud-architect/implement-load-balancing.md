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


---

↩️ [BACK](../gcp.md)
