---
layout: essay
type: essay
title: Introduction to Play
# All dates must be YYYY-MM-DD format!
date: 2015-03-10
labels:
  - Java
  - Play
---

At long last, I have finally started using the [Play Framework](https://playframework.com/) with something vaguely approximating a modicum of competence.  In practical terms, this means that I can make static pages that do not make Internet browsers crash.  The Play Framework allows developers to use Java (and Scala) in conjunction with HTML, CSS, and JavaScript to make web applications, though for the time being I have only managed to make web pages that display predefined content without any use of databases or user interaction.  As usual, I performed a series of programming exercises while learning how to work in Play; due to general sleep deprivation, these are all converted from previous learning exercises.  

## A Simple Play Project 
First of course, I had to install and set up Play.  As might be expected, this configuration took a very long time, was fraught with errors, and was not counted in the elapsed time for this exercise.  Setting up the PATH on my Windows machine to work with [Typesafe Activator](http://typesafe.com/community/core-tools/activator-and-sbt) was unusually difficult as I was unable to put the directories for Activator and [SWI-Prolog](http://www.swi-prolog.org/) in the PATH simultaneously for reasons unknown; on the positive side, this gives me an excuse to not have to use Prolog ever again<sup>1</sup>.

<img class="ui image medium centered floated rounded" src="/images/project-auto-import.png">

Once Play was configured, I started my timer and began to set up a simple Play project in IntelliJ IDEA.  Since this was my first time doing so, IntelliJ required a fair amount of time to load all of the necessary libraries and such; I also learned that it was necessary to check the *Use auto-import* check box during project setup to properly import all of the libraries for Play.  Still, it ultimately took me only 20:38.26 to finish this the first time through, much of which was due to the aforementioned configuration and an unusual and unreproducible error where moving the testing code into a <code>test</code> package broke all of the references to other files in the project.

Because of these other issues not related to Play itself, I decided to repeat the exercise.  As expected, the time needed to repeat all the steps above decreased significantly due to the fact that IntelliJ and Play had already downloaded all of the files and libraries necessary as well as general familiarity with the process.  However, I never managed to fully complete the exercise on subsequent attempts due to an attempt to follow proper Java coding standards: although I am not particularly familiar with how Scala works, I know enough about Java coding standards to recognize that class names should be written in title case, and Play generates views with lowercase file names (ex. index.scala.html) that are then compiled into Java classes with the same name.  It is debatable whether it is proper to follow the Java conventions or the style of the original Play templates; I chose the former, and this resulted in several minutes of frustration as every attempt to refactor the code broke the system in multiple places even when there were no apparent compiler errors.  Eventually, I decided that it was not worth expending further energy on this (the principle of adhering to the style of the original code is much easier to enforce when it is so much more difficult to deviate from the given style); my final attempt without trying to change the capitalization of the files is available at <https://github.com/bsogata/clean-play-java> and took 11:22.88.

## Browser History
When I woke up the next morning, I discovered that someone had already created a template Play project with title-cased view names:


<https://github.com/ics613s15/ics-play-bootstrap>


This reinforced my belief that it is usually better to have other people do your work for you.  This template served as the base for the remaining exercises, the first of which was to redo the [Browser History project](https://github.com/bsogata/browserhistory) in Play.  This was not particularly difficult; as with the basic Play project, most of the 18:01.71 needed to complete this was consumed in waiting for IntelliJ to set up the Play environment, and since this was basically redoing a previous project all of the HTML and CSS was already present.  My code for this exercise is available at <https://github.com/bsogata/playbootstrapbrowserhistory>.

Oddly, the .idea directory is still present in this repository despite the fact that the .gitignore specifically instructs Git not to include the .idea directory.

## Multi-Page Browser History
I then built upon the previous experience to redo [the multi-page layout for the Browser History project](https://github.com/bsogata/browserhistory/tree/multipage).  This was slightly more time-consuming due to the need to create separate pages for each browser reviewed: it is necessary to make the project again in order to have Play create the Java class corresponding to a particular view, and since I had to make multiple pages I ended up waiting a fair amount of time for the build process to complete.  In the end though, this took 23:39.09, and the resulting branch on GitHub is at <https://github.com/bsogata/playbootstrapbrowserhistory/tree/multipage-1>.


## Kamanu
Finally, I converted [my previous work on replicating the Kamanu Composites website into a Play project](https://github.com/bsogata/responsivekamanu).  This was actually a bit easier than the previous exercise since there was only one page to tend to and working with images was the only new topic I had to address.  This took 17:51.99, and my repository for this exercise is available at <https://github.com/bsogata/playresponsivekamanu>.

## Conclusion
My next step will be to use Play with dynamic web pages, actually receiving user input rather than simply displaying information, and after the work above I should be ready to handle those tasks.  Play itself works fine, if somewhat slow in IntelliJ (a recurring trend with everything I try to do in IntelliJ that only appears when I am trying to record the time necessary for me to complete something); obviously it seems a bit too sophisticated for the exercises that I did for this post because Play was designed with far more advanced applications in mind.  
Aside from the Play framework itself and the conflict between existing coding standards for Java and the style for Play-generated view files, my experiences here also bring into question how valuable the repetition of these exercises might be.  Obviously, repeating a task or exercise will help internalize that process and make it easier to recall later.  However, I am fairly certain that I learned very little from my repeated failures when attempting to change the file names for the views in Play, aside from the fact that my new motto in life should be "if at first you don't succeed, destroy all evidence that you tried."

1: The author had to use Prolog the following semester, and that particular love-hate relationship is still ongoing.