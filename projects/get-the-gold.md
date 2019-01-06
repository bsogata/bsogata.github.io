---
layout: project
type: project
image: images/get-the-gold.jpg
title: Get the Gold
permalink: projects/get-the-gold
# All dates must be YYYY-MM-DD format!
date: 2010-12-16
labels:
  - Common Lisp
  - Artificial Intelligence
  - Multi-Agent Systems
summary: An adaptation of the Wumpus World to use a multi-agent environment.
---

Get the Gold (an unofficial name) was a project for ICS 461 (Artificial Intelligence) in the Fall 2010 semester.  I worked with Derek Hirano and Mark Munar on this project, which modified the AIMA code from our (textbook)[http://aima.cs.berkeley.edu/] in order to examine a multi-agent environment.  The project code was written entirely in Common Lisp.

The original AIMA code included an environment called the Wumpus World.  In this world, there was a hero who had to navigate through a matrix to find some gold using only percepts of adjacent cells.  To make the task more difficult, the world could contain pits in which the hero could fall and a stationary monster called a wumpus that would kill the hero if they were in the same cell.  In turn though, the hero carried a single arrow that could be used to kill the wumpus from afar.  This was a single-agent environment: there was one hero and thus only one entity moving around and performing actions.

Get the Gold altered this code to produce a multi-agent environment in which as many as three distinct types of agent could interact with one another.  All three of these types of agent competed for the gold, but two of these agents were programmed to cooperate in obtaining the gold: if one of them managed to take the gold, both would win.

My primary role in this project was in programming the B agent.  (This was at least in part due to the fact that my given name begins with "B".)  The B agent was the most similar to the wumpus in the original code in that it had to be in the same tile as another agent in order to attack.  However, B agents also differed from the wumpus in significant ways.  Most notably, multiple B agents could exist in the same environment whereas the original Wumpus World only allowed for a single wumpus.  B agents could also move around, unlike the immobile wumpus.  The greatest advantage that the B agent had though was access to alcohol.  This alcohol gave B agents the chance to respawn once killed; an alternate explanation was that the B agents were too drunk to realize that they ought to be dead.  The downside of this ability though was that B agents would much rather drink alcohol than actively pursue the other agents or even the gold.

The main thing I gained from this project was the experience of standardized programming in a group.  I had been in at least one group project involving programming before (coincidentally also in Common Lisp), but in that project we started from scratch and thus had to write everything ourselves.  This inevitably resulted in a terribly disorganized mess when we tried to put everything together, and I remember that we spent more time trying to incorporate the work that everyone had done into a single program than we had taken to write our own individual parts.  However, Get the Gold was based on the AIMA code, so there was already a framework and a standard format for us to follow.  This made working on the project much smoother.

In hindsight, this project also demonstrated the importance of quality documentation along with the limitations of that documentation.  For several years, the code for this project has been provided with the disclaimer that the code might not work.  This was due to the fact that I could not make the code work again myself: I could not find any instructions on how to actually run the code or any of our tests.  It was not until I started migrating this portfolio to GitHub Pages that I realized two key points:

* The /doc directory actually includes all of the documentation on how to configure the AIMA code
* One of the reports that I linked to on the project page itself included step-by-step instructions showing the reader how to run our code

Although I certainly concede that taking eight years to realize this has more to do with my limited intellectual faculties than software engineering, it is nevertheless important to remember that documentation is useless if no one reads it.  Developers are often inclined to look first - and sometimes only - at the source code for documentation, and that is why writing comments within the source code itself is critical.

The GitHub site for this project (with all of its flaws intact) is available at:
https://github.com/bsogata/get-the-gold

Other resources for Get the Gold include:
[Presentation Slides](https://bsogata.github.io/projects/GetTheGoldPresentation.pdf)
[Report](https://bsogata.github.io/projects/GetTheGoldReport.pdf)