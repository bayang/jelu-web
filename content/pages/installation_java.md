---
title: Installation from jar.
date: Last Modified 
permalink: /installation/jar/index.html
eleventyNavigation:
  key: installation-jar
  order: 101
  title: Installation from jar.
  parent: installation
---

## Jelu can be run from the jar : 

!!! warning
    Jelu needs at least Java 11 



* download the java Jar from the github releases section in a dedicated folder
* go to this folder
* start the jar (it is a spring fat jar so dependencies are included) : eg 

 ```shell
 java -jar jelu-0.17.0.jar
```
* If you want to tweak the default config (see `src/main/resources/application.yml` in the github repo for example), just create a yaml file called application.yml in the same folder as the jar.
 
For example if you want the database to be located next to the jar file (instead of being located in the default `${user.home}/.jelu/database/` folder) :

```yaml
jelu:
  database:
    path: .
```

The automatic metadata online search is provided for the moment through a calibre tool called fetch-ebook-metadata.

So if you want to use it with the java install, provide the path to the executable in the config, like so : 

```yaml
jelu:
  metadata:
    calibre:
      path: /usr/bin/fetch-ebook-metadata
```


Then open the web UI in your web browser at `localhost:11111`


Concerning Cors, the default is to accept everything, which you might not not want to do.

No config in the config file is equivalent to : 

```yaml
jelu:
  cors.allowed-origins:
    - "*"
```
If you want to secure your instance and narrow the allowed origins, update the config with the desired origins like so : 

```yaml
jelu:
  cors.allowed-origins:
    - https://jelu.myserver.org
```

!!! tip defaults : 


The default config for java, taken from the `src/main/resources/application.yml` file is : 


```yaml
jelu:
  database:
    path: ${user.home}/.jelu/database/
  files:
    images: '${user.home}/.jelu/files/images/'
    imports: '${user.home}/.jelu/files/imports/'
  session:
    duration: 604800 #7 days
```

