---
title:        "Create your own PaaS with Dokku and DigitalOcean"
description:  ""
image:        ""
author:       "sarbull"
---

## Description
Dokku is the smallest PaaS implementation you've ever seen. It can be seen like a personal Heroku infrastructure.

## Create a DigitalOcean droplet
Create a instance with the latest stable Ubuntu. It is recommended to use at least 1GB of RAM, but you can also use SWAP Memory to increase the RAM and since it's SSD it will work very fast.

## Install Dokku on Ubuntu
```bash
$ wget https://raw.githubusercontent.com/dokku/dokku/v0.10.5/bootstrap.sh
$ sudo DOKKU_TAG=v0.10.5 bash bootstrap.sh
```

## Add 1GB of SWAP Memory
```bash
$ sudo swapon --show
$ free -h
$ df -h
$ sudo fallocate -l 1G /swapfile
$ sudo chmod 600 /swapfile
$ sudo mkswap /swapfile
$ sudo swapon /swapfile
$ sudo swapon --show
$ free -h
$ sudo cp /etc/fstab /etc/fstab.bak
$ echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
$ cat /proc/sys/vm/swappiness # 60
$ sudo sysctl vm.swappiness=10 # vm.swappiness = 10
$ sudo vim /etc/sysctl.conf # add vm.swappiness=10
$ cat /proc/sys/vm/vfs_cache_pressure # 100
$ sudo sysctl vm.vfs_cache_pressure=50 # vm.vfs_cache_pressure = 50
$ sudo vim /etc/sysctl.conf # vm.vfs_cache_pressure=50
$ sudo reboot
```

## Deploy a simple application
### Dokku app required instances
```bash
$ ssh root@DROPLET_IP
$ dokku apps:create ruby-rails-sample
$ dokku plugin:install https://github.com/dokku/dokku-postgres.git
$ dokku postgres:create rails-database
$ dokku postgres:link rails-database ruby-rails-sample
```

### Ruby on Rails sample app push to dokku instance
```bash
$ git clone git@github.com:heroku/ruby-rails-sample.git
$ cd ruby-rails-sample
$ git remote add dokku dokku@DROLET_IP:ruby-rails-sample
$ git push dokku master
```
