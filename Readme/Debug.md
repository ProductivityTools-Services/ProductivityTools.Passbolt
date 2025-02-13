sudo nano /etc/nginx/nginx.conf
commented include /etc/nginx/conf.d/*.conf


sudo ufw allow 82/tcp
sudo ufw status



sudo nginx -t
sudo nginx -s reload

I removed the default.conf