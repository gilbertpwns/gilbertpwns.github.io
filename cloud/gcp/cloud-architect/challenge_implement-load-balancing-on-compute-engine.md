# Implement Load Balancing on Compute Engine: Challenge Lab

student-03-a4fe3d727d37@qwiklabs.net
onXV2F3kFkkE
qwiklabs-gcp-03-0c02160ff98e
nucleus-jumphost-886
grant-tcp-rule-919

student-03-a4fe3d727d37@qwiklabs.net
onXV2F3kFkkE
qwiklabs-gcp-03-0c02160ff98e
nucleus-jumphost-886
grant-tcp-rule-919

gcloud auth list

gcloud config list project

gcloud config set compute/region europe-west1

gcloud config set compute/zone europe-west1-b

gcloud compute instances list –project qwiklabs-gcp-03-0c02160ff98e

10.132.0.2
104.155.42.80



--- web servers

```
  gcloud compute instances create nucleus-webserver1 \
    --zone=europe-west1-b \
    --tags=network-lb-tag \
    --machine-type=e2-medium \
    --image-family=debian-11 \
    --image-project=debian-cloud \
    --metadata=startup-script='#!/bin/bash
      apt-get update
      apt-get install nginx -y
      service nginx restart
      echo "
<h3>Web Server: www1</h3>" | tee /var/www/html/index.html'
```

--- Web server 1 output
Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-03-0c02160ff98e/zones/europe-west1-b/instances/nucleus-webserver1].
NAME: nucleus-webserver1
ZONE: europe-west1-b
MACHINE_TYPE: e2-medium
PREEMPTIBLE: 
INTERNAL_IP: 10.132.0.3
EXTERNAL_IP: 104.155.112.117
STATUS: RUNNING


```
gcloud compute instances create nucleus-webserver2 \
    --zone=europe-west1-b \
    --tags=network-lb-tag \
    --machine-type=e2-medium \
    --image-family=debian-11 \
    --image-project=debian-cloud \
    --metadata=startup-script='#!/bin/bash
      apt-get update
      apt-get install nginx -y
      service nginx restart
      echo "
<h3>Web Server: www2</h3>" | tee /var/www/html/index.html'
```

--- LB Template

gcloud compute instance-templates create lb-backend-template \
   --region=europe-west1 \
   --network=default \
   --subnet=default \
   --tags=allow-health-check \
   --machine-type=e2-medium \
   --image-family=debian-11 \
   --image-project=debian-cloud \
   --metadata=startup-script='#!/bin/bash
     apt-get update
     apt-get install nginx -y
     a2ensite default-ssl
     a2enmod ssl
     vm_hostname="$(curl -H "Metadata-Flavor:Google" \

http://169.254.169.254/computeMetadata/v1/instance/name)"
     echo "Page served from: $vm_hostname" | \
     tee /var/www/html/index.html
     systemctl restart nginx'

---	 MIG Template
	
gcloud compute instance-groups managed create lb-backend-group \
--template=lb-backend-template --size=2 --zone=europe-west4-a

--- FW Rule

gcloud compute firewall-rules create grant-tcp-rule-919 \
  --network=default \
  --action=allow \
  --direction=ingress \
  --source-ranges=10.164.0.0/22,34.34.0.0/16 \
  --target-tags=allow-grant-tcp-rule-919 \
  --rules=tcp:80
  
--- Global static external

gcloud compute addresses create lb-ipv4-1 \
  --ip-version=IPV4 \
  --global
 
--- Validate IPV4

gcloud compute addresses describe lb-ipv4-1 \
  --format="get(address)" \
  --global
  
34.110.159.170

--- Create basic health check for HTTP (port 80)

gcloud compute health-checks create http http-basic-check \
  --port 80
  
---create backend service and add instance group as the backend service group with named port (http:80) <-- what?!

gcloud compute backend-services create web-backend-service \
  --protocol=HTTP \
  --port-name=http \
  --health-checks=http-basic-check \
  --global
  
--- add instance group as the backend to the backend service

gcloud compute backend-services add-backend web-backend-service \
  --instance-group=lb-backend-group \
  --instance-group-zone=europe-west4-a \
  --global
  
--- create URL map

gcloud compute url-maps create web-map-http \
    --default-service web-backend-service
	
--- create a target http proxy to route requests to your URL map

gcloud compute target-http-proxies create http-lb-proxy \
    --url-map web-map-http

--- create forwarding rule

gcloud compute forwarding-rules create http-content-rule \
   --address=lb-ipv4-1\
   --global \
   --target-http-proxy=http-lb-proxy \
   --ports=80
---

↩️ [BACK](../cloud-architect/README.md)
