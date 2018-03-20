# docker-wekan-letsencrypt
Automaded docker wekan for nginx proxy (webproxy) integrated with LetsEncrypt

# Automated docker Wekan for nginx proxy (webproxy) integrated with LetsEncrypt

This repo allows you to set up the great [Wekan](https://wekan.github.io) as a container over SSL auto generated and auto renewed by our Web Proxy.

# Prerequisites

In order to use this compose file (docker-compose.yml) you must have:

1. docker [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)
2. docker-compose [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)
3. docker-compose-letsencrypt-nginx-proxy-companion [https://github.com/evertramos/docker-compose-letsencrypt-nginx-proxy-companion](https://github.com/evertramos/docker-compose-letsencrypt-nginx-proxy-companion)

# How to use

1. Clone this repository:

```bash
git clone https://github.com/Mickooz/docker-wekan-letsencrypt.git
```

2. Make a copy of our .env.sample and rename it to .env:

Update this file with your preferences.

```bash
#
# Configuration for Wekan using NGINX WebProxy
#

# Containers name
DB_CONTAINER_NAME=wekan-db
APP_CONTAINER_NAME=wekan

# MongoDB settings

MONGO_URL=mongodb://wekan-db


# Wekan local data path
LOCAL_DB_DIR=/home/user/wekan/wekan-db
LOCAL_DB_DUMP_DIR=/home/user/wekan/wekan-db-dump

# Host 
VIRTUAL_HOST=wekan.yourdomain.com
LETSENCRYPT_HOST=wekan.yourdomain.com
LETSENCRYPT_EMAIL=your_email@yourdomain.com

#
# Network name
# 
# Your container app must use a network conencted to your webproxy 
# https://github.com/evertramos/docker-compose-letsencrypt-nginx-proxy-companion
#
NETWORK=webproxy
```

3. Start your container

```bash
$ docker-compose up -d
```

> This container must be in a network connected to your webproxy containers or use the same network of the webproxy.

> Please keep in mind that when starting for the first time it may take a few moments (even a couple minutes) to get your Let's Encrypt certificates generated.

### For more information about Wekan, check [Wekan Documentation](https://github.com/wekan/wekan/wiki)
