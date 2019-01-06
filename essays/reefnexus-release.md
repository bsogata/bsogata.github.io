---
layout: essay
type: essay
title: ReefNexus Release
# All dates must be YYYY-MM-DD format!
date: 2015-05-13
labels:
  - Project Management
  - ReefNexus
---

Over the past week, the [ReefNexus](https://github.com/ReefNexus/reefnexus) team has focused on cleaning up some of the errors present in our project.  As noted in [my previous post](/essays/sleep-deprivation), there were a lot of errors to deal with.  The most important part of course was actually [getting the database to work on Heroku](https://github.com/ReefNexus/reefnexus/issues/26); I started work on identifying the source of the problem while Danny ultimately fixed the issue.  I wrote a little bit of code implementing the functionality to [search for locations](https://github.com/ReefNexus/reefnexus/issues/19) from the Location view.  Finally, [I updated the Developer Guide](https://github.com/ReefNexus/reefnexus/issues/29) to include instructions on how to install and use PostgreSQL with our system along with an accurate ER diagram.  

These updates were relatively minor; aside from fixing the database though, much of the work had already been completed as of previous milestones.  The deployed and functional ReefNexus application is available at <http://www.reefnexus.com>.  It is entirely possible that there are other defects in the application that we need to fix (in fact, it is very possible that this is the case since I still have an open issue in GitHub to take care of), but for now it appears that ReefNexus is ready for release.  