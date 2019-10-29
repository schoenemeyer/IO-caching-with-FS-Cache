# IO-caching-with-FS-Cache

FS-Cache is a persistent local cache that can be used by file systems to take data retrieved from over the network and cache it on local disk. This helps minimize network traffic for users accessing data from a file system mounted over the network (for example, NFS).    
https://github.com/schoenemeyer/IO-caching-with-FS-Cache/blob/master/pictures/fs-cache.png

https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/storage_administration_guide/ch-fscache


# How to install on a CentOS 7.x

Install package cachefilesd
```
sudo yum install cachefilesd
```
Activate the FS-Cache Service
```
sudo systemctl enable cachefilesd.service
```
You can look at the basic configuration in the file /etc/cachefilesd.conf

Start the service with 
```
sudo service cachefilesd start
```
Check whether service was started correctly
```
sudo service cachefilesd status
```
The output will look like this:
```
(base) [thomas@localhost ~]$ sudo service cachefilesd status [sudo] password for thomas:
Redirecting to /bin/systemctl status cachefilesd.service 
● cachefilesd.service - Local network file caching management daemon
    Loaded: loaded (/usr/lib/systemd/system/cachefilesd.service;
enabled; vendor preset: disabled)
    Active: active (running) since Tue 2019-10-29 08:44:45 CET; 47min ago
   Process: 9213 ExecStartPre=/sbin/modprobe -qab cachefiles (code=exited, status=0/SUCCESS)
  Main PID: 9226 (cachefilesd)
     Tasks: 1
    Memory: 220.0K
    CGroup: /system.slice/cachefilesd.service
            └─9226 /usr/sbin/cachefilesd -n -f /etc/cachefilesd.conf

Oct 29 08:44:45 localhost.localdomain systemd[1]: Starting Local network file caching management daemon...
Oct 29 08:44:45 localhost.localdomain systemd[1]: Started Local network file caching management daemon.
Oct 29 08:44:45 localhost.localdomain cachefilesd[9226]: About to bind cache Oct 29 08:44:45 localhost.localdomain cachefilesd[9226]: Bound cache Oct 29 08:44:45 localhost.localdomain cachefilesd[9226]: Daemon Started
(base) [thomas@localhost ~]$
```
per default FS-Cache uses the directory Verzeichnis /var/cache/FS-Cache , this can be changed .

