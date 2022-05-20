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
      - ~/jelu/config:/config
      - ~/jelu/database:/database
      - ~/jelu/files/images:/files/images
      - ~/jelu/files/imports:/files/imports
      - /etc/timezone:/etc/timezone:ro
    ports:
      - 11111:11111
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

!!! warning
    ARM versions must add this environment variable for automatic metadata fetching : 
    `JELU_METADATA_CALIBRE_PATH=/usr/bin/fetch-ebook-metadata`

