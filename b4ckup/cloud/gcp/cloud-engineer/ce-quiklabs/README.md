# Google Cloud QuikLabs

* [A Tour of Google Cloud Hands-on Labs](./ATOGCHOL.md)

## Preparing for your Professional Cloud Network Engineering Journey

* [GSP073]

    qwiklabs-gcp-04-aefb37ad7ca5

* [GSP074]

gcloud storage buckets create gs://<YOUR-BUCKET-NAME>
gcloud storage buckets create gs://qwiklabs-gcp-01-6e23de429edf

gcloud storage cp ada.jpg gs://YOUR-BUCKET-NAME
gcloud storage cp ada.jpg gs://qwiklabs-gcp-01-6e23de429edf

gcloud storage cp -r gs://YOUR-BUCKET-NAME/ada.jpg .
gcloud storage cp -r gs://qwiklabs-gcp-01-6e23de429edf/ada.jpg .

gcloud storage cp gs://YOUR-BUCKET-NAME/ada.jpg gs://YOUR-BUCKET-NAME/image-folder/
gcloud storage cp gs://qwiklabs-gcp-01-6e23de429edf/ada.jpg gs://qwiklabs-gcp-01-6e23de429edf/image-folder/

gcloud storage ls gs://YOUR-BUCKET-NAME
gcloud storage ls gs://qwiklabs-gcp-01-6e23de429edf

gcloud storage ls -l gs://YOUR-BUCKET-NAME/ada.jpg
gcloud storage ls -l gs://qwiklabs-gcp-01-6e23de429edf/ada.jpg

Make publically available

gsutil acl ch -u AllUsers:R gs://YOUR-BUCKET-NAME/ada.jpg
gsutil acl ch -u AllUsers:R gs://qwiklabs-gcp-01-6e23de429edf/ada.jpg

URL to bucket: https://storage.googleapis.com/qwiklabs-gcp-01-6e23de429edf/ada.jpg [deprecated]

Remove public access

gsutil acl ch -d AllUsers gs://YOUR-BUCKET-NAME/ada.jpg
gsutil acl ch -d AllUsers gs://qwiklabs-gcp-01-6e23de429edf/ada.jpg

Delete objects

gcloud storage rm gs://YOUR-BUCKET-NAME/ada.jpg
gcloud storage rm gs://qwiklabs-gcp-01-6e23de429edf/ada.jpg

* [GSP064]

student 1: student-00-2d396d3825a7@qwiklabs.net
student 2: student-00-3640c29e75cb@qwiklabs.net

create a bucket: qwiklabs-gcp-03-ab3ffa5b0b15

gsutil ls gs://[YOUR_BUCKET_NAME]
gsutil ls gs://qwiklabs-gcp-03-ab3ffa5b0b15

* [GSP089]

gcloud config set compute/zone "us-east1-c"
export ZONE=$(gcloud config get compute/zone)

gcloud config set compute/region "us-east1"
export REGION=$(gcloud config get compute/region)

Run the Monitoring agent install script command in the SSH terminal of your VM instance to install the Cloud Monitoring agent:

curl -sSO https://dl.google.com/cloudagents/add-google-cloud-ops-agent-repo.sh

* [GSP081]

A Cloud Run function is a piece of code that runs in response to an event, such as an HTTP request, a message from a messaging service, or a file upload. Cloud events are things that happen in your cloud environment. These might be things like changes to data in a database, files added to a storage system, or a new virtual machine instance being created.

Since Cloud Run functions are event-driven, they only run when something happens. This makes them a good choice for tasks that need to be done quickly or that don't need to be running all the time.

For example, you can use a Cloud Run function to:

automatically generate thumbnails for images that are uploaded to Cloud Storage.
send a notification to a user's phone when a new message is received in Pub/Sub.
process data from a Cloud Firestore database and generate a report.
You can write your code in any language that supports Node.js, and you can deploy your code to the cloud with a few clicks. Once your Cloud Run function is deployed, it will automatically start running in response to events.

This hands-on lab shows you how to create, deploy, and test a Cloud Run function using the Google Cloud console.

* [GSP080]

qwiklabs-gcp-01-a46f2ccafd5e

view logs

gcloud functions logs read nodejs-pubsub-function \
  --region=us-central1 

* [GSP096]
As stated earlier, Pub/Sub is an asynchronous global messaging service. There are three terms in Pub/Sub that appear often: topics, publishing, and subscribing.

A topic is a shared string that allows applications to connect with one another through a common thread.

Publishers push (or publish) a message to a Cloud Pub/Sub topic.

Subscribers make a "subscription" to a topic where they will either pull messages from the subscription or configure webhooks for push subscriptions. Every subscriber must acknowledge each message within a configurable window of time.

To sum it up, a producer publishes messages to a topic and a consumer creates a subscription to a topic to receive messages from it.

* [GSP095]

```
gcloud pubsub topics create myTopic

gcloud pubsub topics create Test1
gcloud pubsub topics create Test2

gcloud pubsub topics delete Test1
gcloud pubsub topics delete Test2

gcloud pubsub topics list

gcloud  pubsub subscriptions create --topic myTopic mySubscription

gcloud  pubsub subscriptions create --topic myTopic Test1
gcloud  pubsub subscriptions create --topic myTopic Test2

gcloud pubsub topics list-subscriptions myTopic
```

## Pub/Sub publishing and pulling a single message

gcloud pubsub topics publish myTopic --message "Hello"

gcloud pubsub topics publish myTopic --message "Publisher's name is <YOUR NAME>"
gcloud pubsub topics publish myTopic --message "Publisher likes to eat <FOOD>"
gcloud pubsub topics publish myTopic --message "Publisher thinks Pub/Sub is awesome"

gcloud pubsub topics publish myTopic --message "Publisher's name is Gilbert"
gcloud pubsub topics publish myTopic --message "Publisher likes to eat Spaghetti"
gcloud pubsub topics publish myTopic --message "Publisher thinks Pub/Sub is awesome"

gcloud pubsub subscriptions pull mySubscription --auto-ack

## Pub/Sub pulling all messages from subscriptions

```
gcloud pubsub topics publish myTopic --message "Publisher is starting to get the hang of Pub/Sub"
gcloud pubsub topics publish myTopic --message "Publisher wonders if all messages will be pulled"
gcloud pubsub topics publish myTopic --message "Publisher will have to test to find out"
```

Add a flag to your command so you can output all three messages in one request.
You may have not noticed, but you have actually been using a flag this entire time: the --auto-ack part of the pull command is a flag that has been formatting your messages into the neat boxes that you see your pulled messages in.

limit is another flag that sets an upper limit on the number of messages to pull.

Wait a minute to let the topics get created. Run the pull command with the limit flag:

```
gcloud pubsub subscriptions pull mySubscription --auto-ack --limit=3
```

* [GSP094]

```
sudo apt-get install -y virtualenv
python3 -m venv venv
source venv/bin/activate
```

```
pip install --upgrade google-cloud-pubsub
git clone https://github.com/googleapis/python-pubsub.git
cd python-pubsub/samples/snippets
```

```
gcloud pubsub topics publish MyTopic --message "Hello"
```

```
gcloud pubsub topics publish MyTopic --message "Publisher's name is Bert"
gcloud pubsub topics publish MyTopic --message "Publisher likes to eat Ravioli"
gcloud pubsub topics publish MyTopic --message "Publisher thinks Pub/Sub is awesome"
```

```
python subscriber.py $GOOGLE_CLOUD_PROJECT receive MySub
```

* [GSP315]


---

### Cymbal Bank's VPC network architecture

* deploy 3 shared VPC networks using subnet from project 
* service projects provided by teams will deploy resources into and use the shared VPC
* assign access to network resources using IAM
    + Shared VPC admin
    + computer network user
    + network admin
    + security admin

![cymbal bank diagram](../../../img/cymbal-bank-diagram.png)

---

Example of standalone VPC

![standalone-vpc](../../../img/standalone-vpc.png)

### Connecting Cymbal Bank's network to Google Cloud

Dedicated interconnect and Partner Interconnect will connect data centers to Google Cloud regions

* mix of regular and high availability configurations
* mix of layer-2 and layer-3 partner interconnect

![dedicated and partner interconnects](../../../img/dedicated-interconnect_partner-interconnect.png)

### Cymbal Bank's Cloud VPN connecting branches and office to closest regions

Cloud VPN connecting branches and offices to closet region

* mix of HA and Classic VPN
* mix of static routing and dynamic routing with BGP and Cloud Routers

![Cloud VPN diagram](../../../img/cloud-vpn-diagram.png)

### Ensuring network availablity and performance

* Layer 7, utilizing global external and regional internal HTTP(S) LBs
* Provides capacity and low latency serving of static and dynamic resources

![Load-balancing-vpc](../../../img/load-balancing-vpc.png)

### Cloud CDN

Cloud CDN caches static resources to increase capacity and reduces latency for static resources

![Cloud CDN](../../../img/cloud-cdn.png)

### Cloud Armor

Provides web-application firewall attack and DDoS protection

![cloud armor](../../../img/cloud-cdn.png)

### Network monitoring and debugging with operations suite

* VPC flow logs
* firewall logs
* cloud monitoring metrics for network activity
* cloud trace for latency across microservices
* logs may be exported to Pubsub, Cloud storage, or BigQuery

## Cymbal Bank networking in Google Cloud

* deploy legacy monolits as managed instance groups of VMs
* deploy new microservices to GKE
* convert some monoliths to microservices and deploy to GKE

![cymbal bank networking](../../../img/cymbal-bank-networking.png)



---

↩️ [BACK](../../../README.md)
