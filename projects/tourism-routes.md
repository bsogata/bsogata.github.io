---
layout: project
type: project
image: images/tourism-routes.png
title: Tourism Routes
permalink: projects/tourism-routes
# All dates must be YYYY-MM-DD format!
date: 2015-05-15
labels:
  - Ruby on Rails
  - Google Maps
  - Web Mining
  - Recommender Systems
summary: A system that uses blogs as a data source to identify popular tourist routes.
---

Finding the shortest route between two points is a solved problem.  Finding the shortest route between many points is NP-hard but still solvable.  Finding the *best* route for a given person can be practically impossible.  Algorithms cannot account for aesthetics: we can assign weights to certain edges in a graph to estimate how much a person might like that path, but that depends on somehow calculating those values.

People frequently write online about their travels to different locales, and Ling-Chih Yao proposed that we use these blog posts as a data set.  My role was to implement her ideas.  I created a web application using Ruby on Rails that looked through blog postings, performed a keyword search, and constructed the route that the author presumably traveled on.  The user could then view and interact with the route through the Google Maps API.

The web application demonstrates that scraping through the Internet to decide upon travel plans is theoretically possible.  However, creating an application of actual value to the user for this purpose remains extremely impractical.  Parsing through dozens of websites to find specific keywords takes a noticeable amount of time, and the time spent waiting for the routes to appear on the map overshadows any perceived benefits from compiling all of the results into a single website.  More advanced algorithms are necessary to account for variance and ambiguity in vocabulary as well as determining the actual route traveled: the fact that the names of places appeared in a certain order does not guarantee that the author visited those locations in that order.  

Nonetheless, this project was useful in developing my software engineering skills.  Simply writing code was certainly useful practice.  However, the experience working with a "client" and using pseudo-Agile techniques was arguably more valuable for me.  

The GitHub site for this project is:

<https://github.com/bsogata/ics-624-tourism-routes>