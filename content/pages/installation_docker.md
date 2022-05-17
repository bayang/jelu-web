---
title: Installation from docker.
date: Last Modified 
permalink: /installation/docker/index.html
eleventyNavigation:
  key: installation-docker
  order: 102
  title: Installation from docker.
  parent: installation
---
## Jelu can be run via docker

An official image is available here : 

https://hub.docker.com/repository/docker/wabayang/jelu

This method is probably the easiest if you are used to it.

The docker image we provide embeds the fetch-ebook-metada executable to automatically import books based on their title, authors or isbn.

The docker image expects config to be mounted in `/config`, the database to be mounted in `/database`, the pictures folder to be mounted in `/files/images` and the imports dir to be mounted in `/files/imports`.

So a sample docker compose would look like that : 

```yaml
version: '3.3'
services:
  jelu:
    image: wabayang/jelu
    container_name: jelu
    volumes:
      - type: bind
        source: ~/jelu/config
        target: /config
      - type: bind
        source: ~/jelu/database
        target: /database
      - type: bind
        source: ~/jelu/files/images
        target: /files/images
      - type: bind
        source: ~/jelu/files/imports
        target: /files/imports
      - type: bind
        source: /etc/timezone
        target: /etc/timezone
        read_only: true
    ports:
      - 11111:11111
    user: "1000:1000"
    environment:
      - MYENV=test
    restart: unless-stopped

```

!!! tip defaults : 


The default environment variables loaded in the Dockerfile are : 


```shell
ENV JELU_DATABASE_PATH="/database/"
ENV JELU_FILES_IMAGES="/files/images/"
ENV JELU_FILES_IMPORTS="/files/imports/"
```

So it means like we said above that you just need to mount `/database`, `/files/images`, `/files/imports` and `/config`

see [Configuration]({{"/configuration/index.html" | url}}) to see what this config means.

The `user: "1000:1000"` line in the dockerfile is not mandatory.

Use it to force permissions on folders.

Make sure to replace `1000` by your own id (you can get it by calling the `id` unix command).

See https://docs.docker.com/compose/compose-file/#user


!!! warning
    ARM versions are built but have not been tested yet !
    Give us some feedback if you try
