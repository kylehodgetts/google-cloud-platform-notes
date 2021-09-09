# Basic Services

List services enabled

`gcloud services list` 

List services available

`gcloud services list --available`

## Google Cloud Storage

### gsutil

Create bucket

`gsutil mb -l northamerica-northeast1 gs://$BUCKET_NAME -p $PROJECT_ID`

[Bucket locations | Cloud Storage | Google Cloud](https://cloud.google.com/storage/docs/locations)

Get labels on bucket

`gsutil label get gs://$BUCKET_NAME`

Set labels on bucket

`gsutil label set bucketlabels.json gs://$BUCKET_NAME`

Change label on bucket

`gsutil label set -l key:value gs://$BUCKET_NAME`

Delete label on bucket

`gsutil label set -d key gs://$BUCKET_NAME`

See if versioning is enabled on a bucket

`gsutil versioning get gs://$BUCKET_NAME`

Turn on versioning

`gsutil versioning set on gs://$BUCKET_NAME`

Copy file to bucket

`gsutil cp $SOME_FILE.txt gs://$BUCKET_NAME`

Give all users read access to file by changing ACL

`gsutil acl ch -u AllUsers:E gs://$BUCKET_NAME/$FILE_NAME`

## Compute Engine

List running compute instances

`gcloud compute instances list`

Create instance with default options + prompt for zone

`gcloud compute instances create myvm`

Delete instance

`gcloud compute instances delete myvm`

## Gcloud

Closely tied with gsutil and bq

- Share same config
- gsutil could have been gcloud storage
- bq could have been gcloud bigquery

gcloud config set <property> <value> to set properties for commands that may need them

Can use flags for individual commands where a property needs to be overidden once

**Configurations - maintain groups of settings and switch between them**

is_active shows which is being used

List all configs - `gcloud config configurations list`

Create new config - `gcloud config configurations create $NAME`

Use config - `gcloud config configurations activate $NAME`

- Use —configuration command to use configs once

### Google compute Lab commands

```jsx
# Check the elected project
gcloud config list

# Show any .ssh folder
pwd
ls
ls -a .ssh

# Get our bearings in Cloud Shell
whoami
hostname
curl api.ipify.org

# Check that we have nothing running
gcloud compute instances list

# Don't create a default VM
# Cancel: gcloud compute instances create myhappyvm

# Look at how to set the machine type
gcloud compute instances create myhappyvm -h
gcloud compute instances create myhappyvm --help
gcloud compute machine-types list

# See how to filter
gcloud topic filters

# Show some free-tier-eligible options
gcloud compute machine-types list --filter="NAME:f1-micro"
gcloud compute machine-types list --filter="NAME:f1-micro AND ZONE~us-west"

# Set our defaults to Los Angeles
gcloud config set compute/zone us-west2-b
gcloud config set compute/region us-west2

# Start our instance
gcloud compute instances create --machine-type=f1-micro myhappyvm
ping -c 3 myhappyvm
ping -c 3 internalipaddress
ping -c 3 externalipaddress

# Connect to the VM
ssh externalipaddress
gcloud compute ssh myhappyvm

# Get our bearings -- Skip?
whoami
hostname
curl api.ipify.org

# Get back to Cloud Shell
exit
curl api.ipify.org

# Look at the Cloud Shell .ssh files
cd .ssh
ls
cat google_compute_engine.pub
head -n 10 google_compute_engine

# Log back onto the VM
gcloud compute ssh myhappyvm

# See that our key is authorized
cd .ssh
ls
cat authorized_keys
cd ..

# Check out the metadata
curl metadata.google.internal/computeMetadata/v1/
curl -H "Metadata-Flavor: Google" metadata.google.internal/computeMetadata/v1/
curl -H "Metadata-Flavor: Google" metadata.google.internal/computeMetadata/v1/project/
curl -H "Metadata-Flavor: Google" metadata.google.internal/computeMetadata/v1/project/project-id
curl -H "Metadata-Flavor: Google" metadata.google.internal/computeMetadata/v1/project/attributes/
curl -H "Metadata-Flavor: Google" metadata.google.internal/computeMetadata/v1/project/attributes/ssh-keys

# Look at some instance metadata
curl -H "Metadata-Flavor: Google" metadata.google.internal/computeMetadata/v1/instance/
curl -H "Metadata-Flavor: Google" metadata.google.internal/computeMetadata/v1/instance/name
curl -H "Metadata-Flavor: Google" metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/
curl -H "Metadata-Flavor: Google" metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/email

# See what gcloud knows
gcloud config list

# Look at our buckets
gsutil ls
gsutil ls gs://storage-lab-cli/

# Attempt to delete the VM from within the VM
gcloud compute instances delete myhappyvm

# Exit back to Cloud Shell and actually delete the VM
exit
gcloud compute instances delete myhappyvm
```

## Sample questions breakdown

Understand

- Determine the key question — the kicker
    - Most cost effective way etc
- Figure out what everything means and think through the data flow

Eliminate

- Get rid of responses that have fake info or other errors
- Get rid of responses that conflict with key question

Evaluate

- Think through the tradeoffs for remaining responses
- Consider both stated and implied dimensions

Choose

- Pick exact number of responses
- Select best options and eliminate the worst ones

Validate

- Make sure responses answer the key question
- Make sure responses don't conflict with any details

## Working with Custom Images on Google Compute Engine Lab

**Create image from base-apache instance using web console.**

Create custom image from base-apache instance using web console:

- Stop the instance
    - Recommended to keep file system integrity
- Go to Compute Engine > Images
- Click **CREATE IMAGE**
- Name image "webserver-base"
- Set *Family* to "webserver"
- In the Source dropdown menu, select **Disk**
- In the Source disk dropdown menu, select **base-apache**
- Click **Create**

**Create image from custom-webpage instance using gcloud command.**

Create image from custom-webpage instance using gcloud command:

- Stop the instance
- Open Cloud Shell
- Enter command to create image from the *custom-webpage* disk, name the image "custom-webpage", and add to the *webserver* image family
    - `gcloud compute images create custom-webpage --source-disk=custom-webpage --source-disk-zone=us-central1-a --family=webserver`
- Verify that image is created and in the appropriate family using the web console

**View images in web console and view 'webserver' image family information in command line.**

View images in web console and view *webserver* image family information in command line:

- In web console, go to Compute Engine > Images
- To describe image family and view latest image, enter command:
    - `gcloud compute images describe-from-family webserver`
- Shown image is the latest version

**Deprecate base image in our 'webserver' image family using command line.**

Deprecate base version using command line:

- First, view process in web console:
    - Go back to Compute Image > Images
    - Place check next to *webserver-base*, and click **DEPRECATE** from the three dot icons on the far right.
    - Set *State* to **Deprecated**, and set *Replacement* as **custom-page-1**
    - Cancel out and do the same thing via command line.
- In Cloud Shell, enter:
    - `gcloud compute images deprecate webserver-base --state DEPRECATED`
- Verify in web console

**Create a new web server from custom image.**

Create a new web server from custom image:

- Go to Compute Engine > VM Instances
- Click **Create Instance**
- Place it in any region and zone you want
- Name the instance "new-web-server"
- Under *Boot disk*, click **Change**
- Click on **Custom images** from the top menu
- Click on **Show deprecated images** to view all images
- Select **custom-webpage**, and click **Select**
- Check the box for **Allow HTTP traffic** under *Firewall* settings
- Click **Create**
- Once the instance is up, click the **external IP address** to verify the new web page works