---
layout: essay
type: essay
title: Coding Standards
# All dates must be YYYY-MM-DD format!
date: 2015-02-10
labels:
  - Coding Standards
  - Software Engineering
---

Adhering to a clearly defined set of coding standards results in a number of benefits when programming.  Consistently following coding standards throughout a project improves the readability and maintainability of the code, as does proper documentation.  Having worked on a fair number of projects where these coding standards were not present or were not consistently applied (both as the one observing others not following the standards and as the one not following standards), I can testify as to the problems that a lack of coding standards can cause.  I primarily use [Elements of Java Style](http://www.amazon.com/Elements-Java-Style-Reference-Library/dp/0521777682/ref=tmm_pap_title_0) as the foundation of my coding style; while it is an older book, the overwhelming majority of the principles within are still relevant.  

Of course, trying to search line by line through the source code to find stylistic violations is a tedious process.  It would certainly be better to initially write code such that it follows all of the coding standards for a project.  However, in some cases it is necessary to apply coding standards to code that has already been written.  As a retired teaching assistant, I have definitely seen a lot of code where this was the case.  This is where automated tools come into play.  I have used Checkstyle in the past, and a long time ago I wrote about using the eclipse-cs plugin in Eclipse, so finding the corresponding Checkstyle plugin for IntelliJ IDEA seemed like a reasonable course of action.

I started with looking at a particular Java source code file (available at <https://github.com/ics613s15/scribble/blob/master/src/Scribble.java>) and applying the coding standards from <u>Elements of Java Style</u> to it by hand.  After several minutes of looking through the code, I was able to find six violations of the aforementioned standards ranging from poor variable names to missing <code>@Override</code> tags.  Once that was done, I went through the same code with the Checkstyle plugin for IntelliJ IDEA to look for the same coding style violations.  This time, it took a total of 16:22.57 to find a significantly larger number of defects, many of which were automatically fixed through the use of the Checkstyle plugin.  

The updated code is available at <code>https://github.com/bsogata/scribble/blob/master/src/Scribble.java</code>, and the specific differences between this and the original code is available at <code>https://github.com/bsogata/scribble/commit/f50f0d8d4bbf9f7cd034881d5e44a310dbb21bed#diff-980528d6014ed63b6651e8d73a2b4c79</code>.  Since the original code was relatively short and simplistic, it is questionable how much this has improved the readability of the code.  Still, it is worth noting that the general principles of following coding standards will definitely be useful on larger projects.  

As a side note, the only complaint I have about the Checkstyle plugin in IntelliJ IDEA is the way that style violations are indicated: the stylistic defect is highlighted in a yellow or tan color.  The default look and feel for IntelliJ IDEA has a white background as shown here:

<img class="ui image medium centered floated rounded" src="/images/intellij-checkstyle-light.png">

In my old age, it is difficult to actually see what line the defect is on.  Switching to the Darcula look and feel makes the stylistic violation (the <code>else return false</code> line) much more visible:

<img class="ui image medium centered floated rounded" src="/images/intellij-checkstyle-dark.png">

This is a bit of a usability issue, and while switching the look and feel is not a terribly difficult task this design is not ideal.