## Setup passbolt directly on a GCE machine

Basic commands to init the cloud
### 
```
glcould auth login
gcloud config set project pwpassbolt1
```

On windows replace grep with findstr 

### Create GCE VM with Ubuntu
```
gcloud compute zones list |grep us-central1
gcloud config set compute/zone us-central1-a
gcloud compute images list |grep 
gcloud compute machine-types list |grep e2-standard
gcloud compute instances create "pwpassbolt" --machine-type "e2-standard-2" --image-project "ubuntu-os-cloud" --image-family "ubuntu-2204-lts" --subnet "default"
gcloud compute instsances delete
gcloud compute instances stop pwpassbolt
gcloud compute instances start pwpassbolt
```

### Nginx
```
sudo apt-get update
sudo apt install nginx -y
curl localhost
```

### Passbolt
```
curl -LO https://download.passbolt.com/ce/installer/passbolt-repo-setup.ce.sh
chmod +x passbolt-repo-setup.ce.sh
sudo ./passbolt-repo-setup.ce.sh 
sudo apt install passbolt-ce-server
```

Enable https and http in the Phanteon (maybe it could be done from cmd)

![](Images/20250129230854.png)

Passbolt should open


![](Images/20250128230057.png)

- MySQL administator username: root
- MySQL administator username: password: pawel123
- Passbolt database user: passboltadmin
- Passbolt databse name: passboltdb
- provide domain for the server
![](Images/20250129230818.png)

![](Images/20250129231158.png)

### email
- Sender name: pawel
- Sender email: productivitytools.tech@gmail.com
- SMTP host: smtp.gmail.com
- Use TLS: yes
- Port: 587
- Authentication method: Username & password
- Username: productivitytools.tech@gmail.com
- Password: google codes genearted on their page
- Client: empty

### Admin user details
- Pawel
- Wujczyk
- Username: pwujczyk@gmail.com

## Setup passbolt on docker on a GCE machine

- Create VM
- Setup Nginx
- Change Nginx so you know from where it was hosted
```
sudo nano /var/www/html/index.nginx-debian.html
```

- Validate if external port is working
- [Install docker](https://docs.docker.com/engine/install/ubuntu/)
```
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
sudo docker run --rm -d -p 80:80 --name my-nginx nginx

```

### reverse proxy

/etc/nginx/conf.d
```
server {
    listen       80;
    #listen  [::]:80;
    server_name testgce.productivitytools.top;

    location / {
        proxy_pass http://10.128.0.6/;
    }
}

server {
    listen       80;
    #listen  [::]:80;
    server_name testdocker.productivitytools.top;

    location / {
        proxy_pass http://10.128.0.6:81/;
    }
}
```


## not fully validated options

## GCE desktop 
Those steps are not necessary 

[tutorial](https://ubuntu.com/blog/launch-ubuntu-desktop-on-google-cloud)
[tutorial2](https://ubuntu.com/blog/launch-ubuntu-22-04-desktop-on-google-cloud)
[remote desktop](https://ubuntu.com/blog/launch-ubuntu-desktop-on-google-cloud)
- gcloud compute ssh --zone "us-central1-a" "pwpassbolt" --project "pwpassbolt1"
- sudo passwd
- sudo apt update
- sudo install tasksel
- wget https://dl.google.com/linux/direct/chrome-remote-desktop_current_amd64.deb
- sudo apt-get install ./chrome-remote-desktop_current_amd64.deb
- sudo apt install slim
- sudo apt install ubuntu-desktop
- sudo snap install chromium
- sudo bash -c ‘echo “exec /etc/X11/Xsession /usr/bin/gnome-session” > /etc/chrome-remote-desktop-session’
- go to https://remotedesktop.google.com/headless and configure connection

### Firewall 
It needs to be confirmed what worked

- sudo ufw allow 80
- gcloud compute firewall-rules create pwhttp --allow tcp:80
- gcloud compute instances add-tags pwpassbolt --tags http-server






Connect through GCP:
- Click SSH from the Pantheon UI.
- Wait a few minutes for it to fail.
- Retry without Identity-Aware Proxy.

Firewall
- sudo ufw allow 80