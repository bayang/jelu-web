---
title: Book detail.
date: Last Modified 
permalink: /usage/book-detail/index.html
eleventyNavigation:
  key: usage-book-detail
  order: 503
  title: Book detail.
  parent: usage
---

![]({{"/content/images/book-detail.jpg" | url}})


* The book detail page provides all the information currently stored in database for a book.
* The authors are clickable and take you to the author detail page
* Clicking tags also take you to that tag page
* When external providers ids are stored in database, direct links to google books, goodreads or amazon are provided
* At the bottom is a timeline of all events for this book
* You can edit events for a book by clicking the `+ event` button at the top right, or you can directly edit an event by double clicking the small book logo on the timeline
* By clicking delete you can delete the book from you list or from the entire database if you are an admin
!!! danger
    it means that in the first case you delete only your user data about this book but the book stays in the database, for other users for example. In the  second case you wipe this book's data from the database potentially erasing a book from other users history
* The edit button allows you to edit this book's data (the technical data, that will be propagated to all users and also your specific data, that only you can see like ; owned, to read, personal notes etc...)
* the star button allows you to create a review, see [Reviews]({{"/usage/reviews/index.html" | url}})
* The magnifying glass button allows you to fetch (or re-fetch) metadata for the current book
