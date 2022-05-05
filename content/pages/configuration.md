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

