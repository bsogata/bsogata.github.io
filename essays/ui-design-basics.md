---
layout: essay
type: essay
title: Basic (not acidic) UI Design
# All dates must be YYYY-MM-DD format!
date: 2015-02-24
labels:
  - HTML
  - CSS
---

After spending the past few weeks reviewing a number of different Java-centric tools, I have decided to transition slightly to a more web-focused aim.  I have a fair amount of experience in Java (or at least would like to think so), but never in web development using Java.  I have begun studying HTML and CSS and will continue to do so over the next couple of weeks in preparation for learning how to use the Play framework.  Of course, with no experience in Play I have no idea if this will be at all useful, but it is traditional for me to expend far more effort than necessary to accomplish my objectives.  As I have done for the past few weeks, my means of learning and practicing these skills is to perform a series of short exercises requiring the use of said skills as detailed below, and I used IntelliJ IDEA and Git throughout.  

## (Mostly) HTML

<img class="ui image medium centered floated rounded" src="/images/e26.png">

The first task I worked on was making an HTML page containing short descriptions of the three major web browsers.  My attempts to make a joke about the recursive nature of reading about Firefox in Firefox have failed.  This process (making the HTML page, not failing to develop a joke) took 15:42.04 to complete, and the code is available at <https://github.com/bsogata/browserhistory>.  This took slightly longer than I had expected, but in hindsight laying the foundation for the page does require a fair amount of time, at least if the page is to be any good.  This is not pure HTML though; I did use a little bit of CSS in order to resize the images used.

## HTML + CSS

<img class="ui image medium centered floated rounded" src="/images/e27.png">

I then continued on to fully implement CSS styles into the page.  This took 5:52.34, during which I apparently thought it best to move away from Times New Roman (the One True Font) in favor of using [Google Fonts](http://www.google.com/fonts), felt that ivory was different enough from white to make it worth changing the default background color, and managed to make Internet Explorer crash.  This work was done on a separate branch at <https://github.com/bsogata/browserhistory/tree/css-1>. 

## HTML + More CSS

<img class="ui image medium centered floated rounded" src="/images/e28.png">

Finally, I added in CSS that changed the layout of elements on the page rather than simply modifying the appearance of those elements.  This mostly goes to show that I am a programmer and not a designer; a navbar is a common design pattern but does not seem to be all that useful when all the links point to elements on the same horizontal level, I managed to use percentile measurements for the navigation elements but not for the three columns, and so forth.  Admittedly, I would not have been able to complete this in 6:28.85 if I had conducted a proper usability study with interviews and user-task matrices.  The resulting code is available at <https://github.com/bsogata/browserhistory/tree/columns-1>.

## Conclusion
I am very good at making web pages that work (where "work" means "sit there doing nothing") and look terrible in a short period of time.  Fortunately, I will be moving on to Twitter Bootstrap next, which will allow me to make my mistakes more efficiently and thus provide me with more time to correct those mistakes.  This is probably the philosophy that I will adopt for the time being: make mistakes early, then correct those mistakes, then correct the corrections of the mistakes, and so on.  (Oddly enough, this is basically equivalent to what I understand of Agile development, so adopting this perspective might be a good thing.) 