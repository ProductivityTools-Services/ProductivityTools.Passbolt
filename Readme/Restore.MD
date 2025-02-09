[tutorial](https://community.passbolt.com/t/restore-backup-ubuntu-20-04/3179)


```
Install passbolt like you would normally using the installation scripts.
Load the data in the database using  mysql -u your_db_user -p your_db_name < backup.sql
Copy the server keys in config/gpg directory and load them in the keyring using gpg import (as described in the installation documentation). Something like: sudo su -s /bin/bash -c "gpg --home=/keyring/location --import /var/www/passbolt/config/gpg/serverkey_private.asc " www-data with --home matching the keyring location defined in passbolt.php if it’s not the default.
Copy your passbolt.php in config directory
Copy the avatars in webroot/img/public/Avatar
```

docker exec -i  pwujczyklearning1-db-1 bash -c 'mysql -u passbolt -p passbolt < backup_1739386665.sql'


interactive
```
sudo docker exec -it pwujczyklearning1-db-1 sh
mysql -u passbolt --password
cd /usr/share/php/passbolt/bin
./cake passbolt send_test_email --recipient=pwujczyk@gmail.com 
su -s /bin/bash -c "./bin/cake passbolt healthcheck" www-data

```

Restore command:
```
cat backup.sql | docker exec -i CONTAINER /usr/bin/mysql -u root --password=root DATABASE
cat backup_1739386665.sql | sudo docker exec -i pwujczyklearning1-db-1  /usr/bin/mysql -u passbolt --password=P4ssb0lt passbolt
```

docker cp  serverkey_private.asc eea39acf800a:/etc/passbolt/gpg/
docker cp  serverkey.asc eea39acf800a:/etc/passbolt/gpg/