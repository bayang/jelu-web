---
title: Metadata fetching.
date: Last Modified
permalink: /usage/metadata/index.html
eleventyNavigation:
  key: metadata
  order: 510
  title: Metadata.
  parent: usage
---


* When you want to add a book to your Jelu database you can use the automatic metadata fetching plugins.
* To get the isbn you can use the built-in barcode scanner

![]({{"/content/images/metadata_form.jpg" | url}})

* There are 4 plugins at the moment.
* 1- the calibre plugin uses the fetch-ebook-metadata binary (see configuration)
* 2- the google books API can be used but you MUST obtain an API key from Google
* 3- the jelu debug plugin is just a debugging tool that prints what parameters are passed to the metadata fetching service, it then let others plugins in the list be called
* 4- the inventaire plugin calls the [inventaire.io](https://inventaire.io) API (see configuration to activate it)
* 5- the databazeknih plugin calls https://www.databazeknih.cz and is suitable for czech and slovakian searches (see configuration to activate it)
* Each plugin can be given a priority
* When you try to fetch metadata the backend will call the plugins in the following order : from highest order value to lowest
* The outcome from the first plugin to yield a result is sent to the caller.
* It is now possible in the UI to change the plugins used and their order on a **_per-request basis_**


![]({{"/content/images/metadata_reorder.jpg" | url}})

!!! tip
    * this is only possible if you have more than 1 metadata plugin configured

!!! danger
    * At the moment the google plugin only works if an isbn is provided


See the [Configuration]({{"/configuration/index.html" | url}}) page to know how to configure plugins.
