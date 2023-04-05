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

### configuring proxy authentication

!!! danger
    * This is for advanced users, use this only if you know what you are doing

| Env variable      | Property       | Usage        |
|-------------------|----------------|--------------|
| JELU_AUTH_LDAP_ENABLED | jelu.auth.ldap.enabled | Activate or not the ldap authent (turn this off if you don't have a ldap server) |
| JELU_AUTH_PROXY_ENABLED | jelu.auth.proxy.enabled | Activate or not proxy authentication |
| JELU_AUTH_PROXY_ADMINNAME | jelu.auth.proxy.adminName | Name of the admin user (*see below*) |
| JELU_AUTH_PROXY_HEADER | jelu.auth.proxy.header | Header which stores the proxy authentication result, defaults to `X-Authenticated-User` if this configuration entry is not set |

In yaml this looks like that : 

```yaml
jelu:
  auth:
    proxy:
      enabled: true
      adminName: "adminuser"
      header: X-Personal-User
    ldap:
      enabled: false
```

#### How does this works :

You typically use this when you want your reverse proxy to handle the authentication part.

When a request hits your reverse proxy, it redirects the user to an authentication mechanism and sets a header containing the user name.

When Jelu receives a request with the header defined in config (or the default one), it first searches in its database to see if a user with this name exists.

If yes, the session is started with this user.

If no, Jelu automatically creates an user with the name.

If the user name is the same as the adminName from the configuration, then the user is created with admin rights.

!!! danger
    * This allows people to bypass security if anyone finds a way to reach your instance without going through your reverse proxy.


### Adding other metadata providers

See the [Metadata]({{"/usage/metadata/index.html" | url}}) page.

For example, it is possible to use Google book API as a metadata provider.


!!! tip
    * You **must** obtain an API key from Google to use the Google API provider
    * This provider will only search if an ISBN is provided


Once you have an API key you can configure it like this : 

```yaml
jelu:
  metadataProviders:  
    - is-enabled: true  
      apiKey: "YOUR-API-KEY-HERE"  
      name: "google"
```

Then restart Jelu.


There is also a debug plugin (which does nothing except printing the parameters in the logs)

The yaml for plugins configuration is shown below : 


```yaml
jelu:
  metadataProviders:
    - is-enabled: true
      apiKey: ""
      order: -100000
      name: "jelu-debug"
    - is-enabled: true
      apiKey: "YOUR_API_KEY_HERE"
      order: -10
      name: "google"
  metadata:
    calibre:
      path: /usr/bin/fetch-ebook-metadata
      order: 50000
```

The google plugin and the jelu-debug plugin names must be the same as in the config above.

If not set the default order priority of the calibre plugin is 1000.

For the other plugins the default order is -1000.

