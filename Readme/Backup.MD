

[tutorial](https://www.passbolt.com/docs/hosting/backup/from-packages/)
```
sudo su -s /bin/bash -c "/usr/share/php/passbolt/bin/cake passbolt sql_export" www-data
```

Data will be placed in 
```
sudo ls /var/lib/passbolt/tmp/cache/database/
```
```
cp /etc/passbolt/gpg/serverkey_private.asc
cp /etc/passbolt/gpg/serverkey.asc
```