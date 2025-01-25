Google PC
- Install gcloud through software center

Phanteon terminal
- gcloud compute zones list |grep us-central1
- gcloud config set compute/zone us-central1-a
- gcloud compute images list
- gcloud compute machine-types list |grep e2-standard
- gcloud compute instances create "pwpassbolt" --machine-type "e2-standard-2" --image-project "ubuntu-os-cloud" --image-family "ubuntu-2204-lts" --subnet "default"