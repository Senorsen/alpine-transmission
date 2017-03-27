# Transmission on Alpine Linux

## docker-transmission

Transmission Daemon Docker Container

Try it out
----------

Change transmission-daemon config:

    docker run -ti senorsen/alpine-transmission vi /etc/transmission-daemon/settings.json

Create:

    mkdir -p /srv/docker/storage/transmission/{downloads,incomplete,resume,blocklists,torrents}

Run the container:

    docker run -d --name transmission \
    -p 9091:9091 \
    -p 51413:51413/tcp \
    -p 51413:51413/udp \
    -e "USERNAME=admin" \
    -e "PASSWORD=password" \
    -v /srv/docker/storage/transmission/downloads:/transmission/downloads \
    -v /srv/docker/storage/transmission/incomplete:/transmission/incomplete \
    -v /srv/docker/storage/transmission/resume:/etc/transmission-daemon/resume \
    -v /srv/docker/storage/transmission/blocklists:/etc/transmission-daemon/blocklists \
    -v /srv/docker/storage/transmission/torrents:/etc/transmission-daemon/torrents \
    senorsen/alpine-transmission

Connect to running container::

    docker exec -ti _name_container_ /bin/sh


```
