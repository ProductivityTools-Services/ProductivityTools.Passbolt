

[tutorial](https://www.passbolt.com/docs/hosting/backup/from-packages/)

## I did not succeed with backup and restore

```
sudo mysql 

 GRANT ALL PRIVILEGES ON passboltdb.* TO root@localhost;
sudo su -s /bin/bash -c "/usr/share/php/passbolt/bin/cake passbolt sql_export" www-data
```

Data will be placed in 
```
sudo ls /var/lib/passbolt/tmp/cache/database/
```
```
sudo cp /etc/passbolt/gpg/serverkey_private.asc
sudo cp /etc/passbolt/gpg/serverkey.asc
```



## Second attempt

```
wget https://raw.githubusercontent.com/passbolt/lab-passbolt-admin-scripts/refs/heads/main/backup.sh
chmod 700 backup.sh
./backup.sh
```


Test email(not working):
```
bash -c “/var/www/passbolt/bin/cake passbolt send_test_email --recipient=pwujczyk@gmail.com”
```