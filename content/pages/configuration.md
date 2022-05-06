---
title: Configuration.
date: Last Modified 
permalink: /configuration/index.html
eleventyNavigation:
  key: configuration 
  order: 200
  title: Configuration.
---
## Configuration


While Jelu is provided with sensible defaults you might want to tune things a bit.

It is possible to provide configuration via environment varibles or via an `application.yml` file.

If you are running the java version put the `application.yml` file next to the jar.

If you are running the docker version either provide environment variables or put an `application.yml` file inside the folder you mounted on `/config`.

### Jelu specific configuration

| Env variable      | Property       | Usage        |
|-------------------|----------------|--------------|
| JELU_DATABASE_PATH | jelu.database.path | Path to a **folder** where the database `jelu.db` will be created |
| JELU_FILES_IMAGES | jelu.files.images | Path to a **folder** where the book covers and authors pictures will be  stored |
| JELU_FILES_IMPORTS | jelu.files.imports | Path to a **folder** where the csv imports will be stored |
| JELU_METADATA_CALIBRE_PATH | jelu.metadata.calibre.path | Path to the calibre fetch ebook metadata binary; eg : `/usr/bin/fetch-ebook-metadata` |
| JELU_CORS_ALLOWED-ORIGINS | jelu.cors.allowed-origins | a list of hosts that should be accepted see [Installation java]({{"/installation/jar/index.html" | url}}) for examples |
| JELU_SESSION_DURATION | jelu.session.duration | Duration of the frontend session in **seconds**, default is 604800 which is 7 days |

### Spring herited configuration

Jelu is developed using the Spring framework and [Spring boot](https://docs.spring.io/spring-boot/docs/current/reference/html/index.html), so all config from spring and spring boot is available.

Here are some configuration keys that may be useful : 

| Env variable      | Property       | Usage        |
|-------------------|----------------|--------------|
| SERVER_PORT | server.port | The port used by the API and the web frontend, default is `11111` |
| SPRING_DATASOURCE_USERNAME | spring.datasource.username | The username of the jelu.db database, default is `jelu_user` |
| SPRING_DATASOURCE_PASSWORD | spring.datasource.password | The password of the jelu.db database, default is `mypass1234` |
