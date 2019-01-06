---
layout: essay
type: essay
title: Hale Aloha CLI
# All dates must be YYYY-MM-DD format!
date: 2011-11-28
labels:
  - Software Engineering
  - Issue Driven Project Management
---

[Hale Aloha CLI](http://code.google.com/p/hale-aloha-cli-teams/) is an interface allowing users to view information concerning energy and power consumption in the Hale Aloha residences on the University of Hawaii at Manoa campus.  For this project, I worked with [Jayson Gamiao](https://www.linkedin.com/in/jaysongamiao) and [Jason Yeo](https://www.linkedin.com/in/jason-yeo-92865967) in a test of Issue Driven Project Management.  In addition, we experimented with a small number of technologies and tools such as Jenkins and Google Code.

IDPM unsurprisingly deals with project management, focusing on keeping project members working on issues that continue progress on the project.  In theory, it might sound like micromanaging the project; in practice it seems to work much better.  In IDPM, each project member receives small tasks to complete.  Each project member should always have at least one task to work on.  These tasks, being small, should take only a couple of days to complete.  This necessitates frequent meetings so that developers have a constant supply of tasks to work on.

In practice, the group followed these guidelines fairly closely.  All three group members were constantly and continuously working on the project from about 15 November, the date of our second group meeting in which we discussed how to work on the project.  The exceptions to this were from 18 to 20 November, during which I was ill, 21 to 23 November, during which the WattDepot server used in the project was nonfunctional and was unable to provide us with data, and 24 November, during which we had to wait for data to accumulate after a server reset.  The tasks (referred to as “issues” in the project site) could have been smaller; many of the tasks took longer than two days to complete.  On the other hand, one could also argue that the tasks only *seem* to have taken more than two days as some group members were reluctant to label tasks as "Done" until their code for those tasks had received extensive testing and peer review.  In addition, as this is the first time any of us have worked with IDPM, there are naturally many mistakes and omissions as we forgot to refer to particular issues in our commit logs. 

After my comments concerning testing for the Robocode project (essentially, that it would be better to incorporate testing early in the development process), this project allowed me to experience what such a project was like.  Throughout this project, any code that I wrote was almost immediately accompanied with a JUnit test.  This was never a tremendous annoyance; rather, the testing allowed me to verify my work long before any real manual testing was possible through the command-line interface. 

As for the project itself, the user is provided with a few commands:

* <code>current-power [source]</code>: Prints the current power consumption of the source.
* <code>daily-energy [source] [date]</code>: Prints the amount of energy that the source consumed on the given date. 
* <code>energy-since [source] [date]</code>: Prints the amount of energy that the source has consumed from the given date to the present.
* <code>rank-towers [date] [date]</code>: Prints the Hale Aloha towers in order of energy consumption between the dates given.
* <code>help</code>: Prints a list of commands that the user may type in. 
* <code>quit</code>: Exits the interface.

Everything works as intended. There are a few features that we had hoped to implement but lacked the time to work on.  In particular, we had considered the use of [reflection](http://java.sun.com/developer/technicalArticles/ALT/Reflection/) to ease the continued expansion of this interface.  This unfortunately never came about. 

Much more detailed information concerning this project is available at the project site.

