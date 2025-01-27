Setup on the Google Cloud

### 
```
glcould auth login
gcloud config set project pwpassbolt1
```

findstr on windows, grep on linux

Phanteon terminal
- gcloud compute zones list |grep us-central1
- gcloud config set compute/zone us-central1-a
- gcloud compute images list |grep 
- gcloud compute machine-types list |grep e2-standard
- gcloud compute instances create "pwpassbolt" --machine-type "e2-standard-2" --image-project "ubuntu-os-cloud" --image-family "ubuntu-2204-lts" --subnet "default"
- gcloud compute instsances delete


[tutorial](https://ubuntu.com/blog/launch-ubuntu-desktop-on-google-cloud)
[tutorial2](https://ubuntu.com/blog/launch-ubuntu-22-04-desktop-on-google-cloud)
- gcloud compute ssh --zone "us-central1-a" "pwpassbolt" --project "pwpassbolt1"
- sudo apt update
- sudo install tasksel
- wget https://dl.google.com/linux/direct/chrome-remote-desktop_current_amd64.deb
- sudo apt-get install ./chrome-remote-desktop_current_amd64.deb
- sudo apt install slim
- sudo apt install ubuntu-desktop
- sudo snap install chromium
- sudo bash -c ‘echo “exec /etc/X11/Xsession /usr/bin/gnome-session” > /etc/chrome-remote-desktop-session’
- go to https://remotedesktop.google.com/headless and configure connection






Connect through GCP:
- Click SSH from the Pantheon UI.
- Wait a few minutes for it to fail.
- Retry without Identity-Aware Proxy.

Firewall
- sudo ufw allow 80