# Jakarta EE app on Liberty running in Podman on RHEL 9

- Install RHEL
- Seet hostname
```
$ sudo -i
[sudo] password for pslucas:
# hostnamectl set-hostname AppSrv01.example.com
# hostname**
AppSrv01.example.com
 ```  
- Register RHEL
```
rhc connect --activation-key ak-rhel-server-liberty --organization ########
Connecting AppSrv01.example.com to Red Hat.
This might take a few seconds.
...
Successfully connected to Red Hat!

Manage your connected systems: https://red.ht/connector
```

- Update RHEL
```
# dnf -y update
Updating Subscription Management repositories.
Last metadata expiration check: 0:11:49 ago on Mon 21 Apr 2025 10:08:21 AM CDT.

...

```
