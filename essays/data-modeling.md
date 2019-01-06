---
layout: essay
type: essay
title: Modeling Behaviors
# All dates must be YYYY-MM-DD format!
date: 2015-04-14
labels:
  - Lucidchart
  - Data Modeling
---

With all the time spent on the ReefNexus project, I decided to work on something comparatively less intensive this past week and experimented with the Lucid Charts plugin for Google Docs.  Amongst a multitude of other features, Lucid Charts allows users to easily draw ER diagrams, and since we will likely be setting up an actual database for ReefNexus in the near future it makes sense for us to have a way to represent the models and relationships within the database.  As usual, I went through a couple of brief exercises to learn how to use the software.

## Library Model
<img class="ui image medium right floated rounded" src="/images/erd-library.png">

My first test was to create a model for a library system.  As shown in the image to the right, this was fairly simple: there are separate entities representing the books in the library, the borrowing or reserving records ("Borrow" was used as it is the more common action, but there is certainly room to use a better name), and the patrons borrowing or reserving the books.  Each book can be borrowed or reserved multiple times (or none at all), but each borrowing record can only refer to a single book.  Similarly, patrons can borrow or reserve multiple times (and again, a specific patron might not have borrowed any books yet and thus would not have any Borrow instances), but each borrowing record only points to a single patron.  

With this model, someone with access to the database can do any of the following:

Action | Explanation 
-------|------------
Check whether a book has been reserved | Find any Borrow instances with a type of "reserved" and a returned value of true
Check which patron borrowed a particular book | Find all Borrow instances with a type of "borrowed" referring to the given book, then find the corresponding Patrons
Check which books a particular patron borrowed | Find all Borrow instances with a type of "borrowed" that point to the given Patron
Check whether a copy of a particular book is currently borrowed | Find all Borrow instances that refer to the Book in question and have not been returned 
Check which reservation should receive a returned book | Find all Borrow instances with type "reserved" that refer to the Book in question, then select the entry with the earliest date that has not been returned
Check the borrowing history of a book | Find all Borrow instances with a type of "borrowed" that refer to the given Book
Check the reservation history a book | Find all Borrow instances with a type of "borrowed" that refer to the given Book

This took 12:39.89 to complete; it did take roughly a minute to download the resulting image to my computer and verify that everything transferred properly into the image shown to the right.  

<img class="ui image medium right floated rounded" src="/images/erd-library.png">

## Car Rental Model
<img class="ui image medium right floated rounded" src="/images/ERD-CarRental - ERD.png">
Next, I modeled something slightly more complex.  A rental car chain might have multiple offices, cars, and customers (otherwise they would not really be a chain).  All of these have their own entities in the diagram to the right, and there is also a table for reservations.  Each location has multiple vehicles while each vehicle can only be at a single location at a time.  Each vehicle has a specific type (economy car, van, box truck, etc.) and can have multiple reservations, whereas each reservation must refer to a single vehicle.  Reservations also have a type which was originally meant to afford distinctions between reservations and rentals; in hindsight, it is unclear whether this is necessary.  (For reference, I do not actually have a driver's license.)  Each reservation has a single customer while a customer can have one or more reservations; this is different from the location-vehicle and vehicle-reservation relationships since it is entirely possible to have a location without vehicles or a vehicle without reservations but not a customer without reservations since the employees of the rental company would not enter data for the customer unless he or she has actually rented a car from them. 

In this model, users can accomplish the following:

Action | Explanation
-------|------------
Add a new customer | Create a new entry in the Customer table
Update customer information | Find the Customer entry, then modify as needed
Reserve a type of vehicle at a given location between a specific start and end time | Find the Location, get a Vehicle at the Location with the given type that has been returned (thus is currently at the Location) and does not have another Reservation, then make a Reservation with the given time to pick up and return that references the Customer making the reservation
Return a vehicle | Find the Vehicle, then update the mileage (odometer), gas (whether the gas tank was refilled), and returned (the most recent date and time the vehicle was returned)

Despite the additional complexity, this took less time than the previous exercise and I finished in 11:25.58.  

## Conclusion
Lucid Charts is a very useful and usable tool: it fulfills its purpose and does so in a clean, elegant manner.  I make no claims as to the correctness of the models that I made above (there are very good reasons why I am not a database administrator), but correcting any mistakes would be a very simple task using Lucid Charts.   The lack of explicit data types in the experiments I performed here may be confusing (especially with the type field that I repeatedly used), but I believe Lucid Charts does offer the option to create boxes with multiple columns, so in future I might put the field name in one column and the intended data type in another.  Thinking of (good) names for entities and fields may also be an issue.