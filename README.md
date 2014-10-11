vagrant-base-php-dev-box
========================

This repo is used to build base PHP development server box for the purpose of easier creation of application dev boxes later.

Based on Ubuntu Trusty 32-bit (14.04) server.

###IMPORTANT: 
NFS is enabled by default, if you are running Windows or see no use for NFS just comment out or remove this line `config.vm.synced_folder ".", "/vagrant", type: "nfs"` from Vagrantfile.


#Packages:

###Core Packages:

####PHP 5.5
####MySQL 5.5
####Nginx

###Additional Packages:

_They will be installed by default, remove them from etc/provisioning/setup.yml if not needed (before running vagrant up!)._

####ElasticSearch
Elasticsearch is a powerful open source search and analytics engine that makes data easy to explore

####Memcached
Free & open source, high-performance, distributed memory object caching system

####Java 7 OpenJDK
Java Runtime Environment, used for assets compilation in Assetic.

###Helper Packages:

_They will be installed by default, remove them from etc/provisioning/usual-packages.yml if you dont need them (before running vagrant up!)._

####dstat
versatile tool for generating system resource statistics 

####joe
JOE is a full featured terminal-based screen editor

####git
Git is a distributed revision control and source code management (SCM) system

####xz-utils
XZ Utils is free general-purpose data compression software with high compression ratio



=====
#Usage

###Boot new server:
```
vagrant up
```

###Create new base box (package):

#####Step 1) Boot vagrant
```
vagrant up
```

#####Step 2) After booting, generate package that will be named trusty32-phpdev with current date suffix
```
vagrant package --output "trusty32-phpdev-$(date +'%Y%m%d').box"
```


#####Step 3) Import box to current server
```
vagrant box add --name "trusty32-phpdev-$(date +'%Y%m%d')" "trusty32-phpdev-$(date +'%Y%m%d').box"
```

###Optional commands:

#####Destroy current box, it's not needed any more.
```
vagrant destroy
```

#####Removing the box from current server (if not needed any more)
```
vagrant box remove "trusty32-phpdev-$(date +'%Y%m%d')"
```


=====
###List of already generated boxes:

2014-10-11 -> http://dwnl.nulldevelopment.hr/boxes/trusty32-phpdev-20141011.box