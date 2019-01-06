---
layout: project
type: project
image: images/course-availability.png
title: Course Availability Website
permalink: projects/course-availability
# All dates must be YYYY-MM-DD format!
date: 2013-12-19
labels:
  - Ruby on Rails
  - Git / GitHub
summary: A web application that notifies students when seats open up in courses they wish to register for.
---

Hansen Cheng and I developed the Course Availability Website for ICS 665 (User Interfaces and Hypermedia) at the University of Hawaii at Manoa.  The project was primarily written in Ruby with some CSS and JavaScript.

The goal of the project was to create a system capable of providing notifications to students at UH Manoa when seats became available for a course.  Since there are a finite number of seats available per course and many of those courses are required for the undergraduate degree, there is often a great deal of competition to get a spot in certain classes.  This web application was designed to let students indicate what courses they wanted to take and then send emails to the users if seats became available for those courses.

My role in this project was primarily on the database side.  I created models for the courses and users along with their corresponding views and controllers.  Since I already knew how to use Ruby on Rails at this point, the project largely served as a review of those skills.  However, I also used the Nokogiri library to parse the course availability data from the UH website and Rufus to send notification emails to users on a scheduled basis.

The GitHub site for this project is:
https://github.com/bsogata/course_availability

Since we finished work on this project, the University of Hawaii has changed its course availabilty system to account for this.  Aside from breaking all of the URLs used in the code, these modifications include an official waitlist for students.  This negates the need for this project since students on the waitlist are automatically notified when seats become available.