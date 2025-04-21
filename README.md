# Jakarta EE app on Liberty running in Podman on RHEL 9

## Pre-reqs  
- Install RHEL
- Switch to root and Set hostname
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

- Update RHEL and reboot the server
```
# dnf -y update
Updating Subscription Management repositories.
Last metadata expiration check: 0:11:49 ago on Mon 21 Apr 2025 10:08:21 AM CDT.
...
Complete!
# reboot now
```

- Intall OpenJDK 21 which is the latest Long Term Support (LTS) version of the OpenJDK
```
# dnf install -y java-21-openjdk-devel
```

- Install conatiner tools
```
# dnf install -y container-tools
Updating Subscription Management repositories.
Last metadata expiration check: 0:03:14 ago on Mon 21 Apr 2025 10:22:52 AM CDT.
```

- Check the Java Installation
```
# java -version
openjdk version "21.0.7" 2025-04-15 LTS
OpenJDK Runtime Environment (Red_Hat-21.0.7.0.6-1) (build 21.0.7+6-LTS)
OpenJDK 64-Bit Server VM (Red_Hat-21.0.7.0.6-1) (build 21.0.7+6-LTS, mixed mode, sharing)
```

- For this tutorial we need Maven 3.8.6 or a later release.  For this tutorial I donwloaded the binary tar.gz archive 3.9.9 from the [Maven Apache Project](https://maven.apache.org/download.cgi).  After you download the Maven, you can move the file from your Downloads directory to the directory of your choice.  I placed the file in the /usr/local file.  Unzip the file there.
```
# mv apache-maven-3.9.9-bin.tar.gz /usr/local/
# cd /usr/local
# tar -xzf apache-maven-3.9.9-bin.tar.gz 

```
- check Maven version
etadata expiration check: 0:17:36 ago on Mon 21 Apr 2025 10:22:52 AM CDT.
...
Complete!
# mvn --version
Apache Maven 3.6.3 (Red Hat 3.6.3-19)
Maven home: /usr/share/maven
Java version: 17.0.15, vendor: Red Hat, Inc., runtime: /usr/lib/jvm/java-17-openjdk-17.0.15.0.6-2.el9.aarch64
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "5.14.0-503.38.1.el9_5.aarch64", arch: "aarch64", family: "unix"
```
- Install git and check git version
```
# dnf install -y git
Updating Subscription Management repositories.
Last metadata expiration check: 0:17:36 ago on Mon 21 Apr 2025 10:22:52 AM CDT.
...
Complete!
# git --version
git version 2.43.5

```

## Getting Started

- Change back to your user and clone the git repository
```
# exit
$ git clone https://github.com/openliberty/guide-getting-started.git
$ cd guide-getting-started
```
