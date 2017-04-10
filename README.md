# Transmission on Alpine Linux

## docker-transmission

Transmission Daemon Docker Container

Try it out
----------

Change transmission-daemon config:

    docker run -ti senorsen/alpine-transmission vi /etc/transmission-daemon/settings.json

And a simple `docker stop` should save settings, too.

Create:

    mkdir -p /srv/docker/storage/transmission/{downloads,etc}

Run the container:

    docker run -d --name transmission \
    -p 9091:9091 \
    -p 51413:51413/tcp \
    -p 51413:51413/udp \
    -e "USERNAME=admin" \
    -e "PASSWORD=password" \
    -v /srv/docker/storage/transmission/downloads:/transmission/downloads \
    -v /srv/docker/storage/transmission/etc:/etc/transmission-daemon \
    senorsen/alpine-transmission:latest

Connect to running container::

    docker exec -ti transmission /bin/sh


