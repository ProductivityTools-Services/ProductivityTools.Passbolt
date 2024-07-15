docker installation is difficult
trying this one
https://www.passbolt.com/docs/hosting/install/ce/ubuntu/

ufw status  
sudo ufw allow 80

## Create first user manually 
[liink](https://community.passbolt.com/t/how-to-create-a-user-manually-in-cli/2118)
Command:

my command:
```
su -s /bin/bash -c "/usr/share/php/passbolt/bin/cake passbolt register_user -u pwujczyk@gmail.com -f pawel -l wujczyk -r admin" www-data
```
internet command


```
su -s /bin/bash -c “/var/www/passbolt/bin/cake passbolt register_user -u email -f firstname -l lastname -r admin” nginx
```

General command:
```
you@passbolt:/var/www/passbolt$ ./bin/cake passbolt register_user --help
```


Restarting the wizard:
```
However if you want to restart the wizard you need to:

    Delete the file located in your passbolt directory: config/passbolt.php
    Make sure config directory is writable
    Delete or create a new database instance
    You can also delete the keys from the keyring (optional)

That should be able to trigger the installation wizard.
```
