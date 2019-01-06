---
layout: essay
type: essay
title: Project Progress
# All dates must be YYYY-MM-DD format!
date: 2015-04-13
labels:
  - Project Management
  - ReefNexus
---

As mentioned previously, I am currently working with Danny Weng and Eric Wu on a project that aims to display information about the populations of fish in Hawaii.  Our GitHub site is still at <https://github.com/wengdg/reefnexus>, but we now also have the application operational at <http://reefnexus.com/><sup>1</sup>.  Of course, by "operational" I mean that we have something that at least runs; it will still take a while for us to fully implement all of the features that we want to include in the final application. 

Our main objective for this first milestone was to implement the ability to view fish data.  We were generally successful in this: users can click on the map to see a list of what fish are in the area, and to make things simpler the application can also automatically detect where the user is.  The application also provides some additional information regarding the locations.

The next step is to give users the ability to input data into the application.  Specifically, as users see fish, they should be able to update the number of fish in that area.  The biggest problems here are how to design the mechanism for user input and how to verify that the data from the user is accurate.  It is impractical for the user to type in the name of the fish found while still in the water, but that provides the application with the most information; on the other extreme, it is theoretically very easy for users to take pictures of fish underwater, but much more difficult for the web application to perform image recognition to attempt to identify the species of fish shown in a picture.  

In the short term though, our primary focus will be on project management rather than development.  Due to the extremely accelerated development of this project in recent days – we basically completed all of the work regarding the locations and fish in about two days – much of our documentation and testing is now very much out of date.  Consequently, we will spend the next couple of days improving the wiki at the GitHub site linked to above and creating a project site using GitHub Pages. 

1: The application is no longer operational.