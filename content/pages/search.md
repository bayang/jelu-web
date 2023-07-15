---
title: Search.
date: Last Modified 
permalink: /usage/search/index.html
eleventyNavigation:
  key: search
  order: 557
  title: Search.
  parent: usage
---

We now have Full Text Search : 

- FTS is case-insensitive
- When searching with CJK characters (Chinese, Japanese, Korean), a minimum of 2 characters is required.
- The order of words is not important: `batman robin` will match `Robin & Batman`
- To search by words in order, enclose your search in `"`: `"white knight"` will not match `knight white` nor `white and knight`
- By default, the search will match the book title, isbn10 and isbn13.
- You can use the `AND`, `OR` and `NOT` operators (UPPERCASE) to build complex queries:
  - `batman NOT publisher:dc` will match all `Batman` series not published by _DC Comics_
  - `batman OR robin` will match `Batman` or `Robin`
  - `tag:fantasy author:guin`

The following fields are available for search using the `field:search` syntax :

- `title` will search the title. Example: `title:"lord"`
- `isbn` will search isbn10 and isbn13. Example: `isbn:"2841720454"`
- `tag` will search any tag. Example: `tag:"fantasy"`
- `author` will search authors. Example: `author:pratchett`
- `translator` will search translators. Example: `translator:couton`
- `series` will search series. Example: `series:lotr`
- `language` will search languages. Example: `language:fr`
- `publishedDate` will search published date. Example: `publishedDate:2020`
- `publisher` will search publisher. Example: `publisher:dc`
- `summary` will search summary. Example: `summary:word`
- `googleId` will search google id. Example: `googleId:1234`
- `goodreadsId` will search goodreads id. Example: `goodreadsId:1234`
- `amazonId` will search amazon id. Example: `amazonId:1234`
- `librarythingId` will search librarything id. Example: `librarythingId:1234`


<sub><sup>(The idea and part of the code comes from Komga implementation, go check it out : https://github.com/gotson/komga)</sub></sup>
