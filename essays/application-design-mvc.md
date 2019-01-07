---
layout: essay
type: essay
title: All Play and No Work
# All dates must be YYYY-MM-DD format!
date: 2015-03-17
labels:
  - Java
  - Play
---

As mentioned in my previous post, my next goal with the [Play Framework](https://playframework.com/) was to create pages that can respond to user input.  This involved adding the "model" part of the MVC design pattern into my knowledge of Play.  As with all the previous posts, I went through a series of exercises to learn and practice how to accomplish this; this time though, these were all cumulative exercises building on one another.  Given the intermittent problems I have had with the slow performance of IntelliJ and Play, it seemed best to minimize the need to switch between projects; this also provided a bit of practice in working with multiple branches (which I definitely needed given that I managed to make a couple of mistakes when merging my work back into the master branch).

## Initial Mockup
I started with a simple application consisting of two pages: an index page containing a table with contact information for various imaginary persons

<img class="ui image medium centered" src="/images/e41-index.png">

and another page on which to input new contacts.

<img class="ui image medium centered" src="/images/e41-newContact.png">

This did not require anything beyond what I had done previously, though creating a form in Bootstrap was somewhat new.  In that respect, the fact that this took 21:38.24 is somewhat disappointing, though I suppose the initial setup for a project will always take a fair amount of time.  The code for the project at this stage is available at <https://github.com/bsogata/digits/tree/47e7c9cbfeee7498738c5a80a018ee87581fd554>. 

## Adding Form Handling
Next, I added the functionality for Play to handle the form through a POST request.  This entailed the creation of a backing class – essentially a Java class existing solely to store contact data as it is transferred between pages.  This took 17:12.49, and the branch with the project at this point is at <https://github.com/bsogata/digits/tree/form-1>.

## Adding (Internal) Validation

<img class="ui image medium centered" src="/images/e43-newContact.png">

The next step was including a means of verifying that the values in the input form were valid.  Although this could be accomplished on the client side, checking the values within the controller is also useful and arguably better (the server side may be assumed to have a better idea of what constitutes a valid value).  This validation occurred in a method placed into the aforementioned backing class.  If any input values were invalid an error message would be displayed and the invalid field would be highlighted in red.  This took 19:29.56 to complete, with the resulting branch available at <https://github.com/bsogata/digits/tree/validate-1>.

## Where Everything Starts to Fall Apart
In theory, this next addition should have been fairly easy: with everything set up in the application, all I had to do was add an actual model.  While there was no actual database set up for the application, making a static class to store all of the contact information served as a temporary measure (and will continue to do so until I learn how to use an actual database management system in conjunction with Play), and actually displaying the contacts really only requires iterating through the list of contacts.  However, it was at this point that having only a cursory understanding of the syntax used throughout the Play framework became a problem, specifically in regards to the intermixing of Java and what I assume to be Scala.  Just trying to get all of the data types to reconcile with one another was a significant issue, and one that I ultimately could not completely solve.  After 33:30.26 of not being able to produce something that could even compile let alone do what it was expected to, I abandoned my first attempt to add a model to the application.

The next day, I began a second trial at adding models to the application.  This turned out to be much more successful; although I did not keep the code from the first attempt, I was at least familiar with the basic processes and managed to implement a working <code>Contact</code> model in around 23 minutes.  The pages loaded up and behaved properly in Firefox, but as I was performing a last test of the system – essentially a regression test, since the tests had not been modified and basically only checked that the pages in the application loaded correctly – I received a message that the application could not compile.  Of course, this made no sense to me initially since the application obviously could compile well enough for Activator to run.  Eventually, I found the source of the compilation error in one of the tests:

<pre>
  /**
   * Tests that the Index template renders correctly.
   */
  @Test
  public void renderTemplate() {
    Content html = views.html.Index.render(ContactDB.getContacts());
    assertThat(contentType(html)).isEqualTo("text/html");
    assertThat(contentAsString(html)).contains("Home");
  }


  /**
   * Tests that the New Contact template renders correctly.
   */
  @Test
  public void renderNewContactTemplate() {
    Content html = views.html.NewContact.render((Form&lt;ContactFormData&gt;) Form.form(ContactFormData.class));
    assertThat(contentType(html)).isEqualTo("text/html");
    assertThat(contentAsString(html)).contains("New Contact");
  }
</pre>

There was and is nothing apparently wrong with this code; the calls to render are exactly the same as those in the controller and thus test the same code that the controllers would execute.  However, the project still refused to compile despite repeated attempts to re-make the project.  Eight minutes later, Play finally recognized that <code>ContactDB.getContacts()</code> did in fact produce a <code>List[Contact]</code> that could serve as a valid parameter to the Index view, but the <code>renderNewContactTemplate</code> still would not compile; the exact error message is <code>render(play.api.data.Form<views.formdata.ContactFormData>)' in '' cannot be applied to '(play.data.Form<views.formdata.ContactFormData>)</code>, and [the solution proposed on Stack Overflow](http://stackoverflow.com/questions/16420128/actual-argument-play-data-form-cannot-be-converted-to-play-api-data-form) is well beyond my limited knowledge of Scala.  In the end, I commented out the <code>renderNewContactTemplate</code> test and committed the model-1 branch at <https://github.com/bsogata/digits/tree/model-1> after 32:00.69 of work.

After resolving to comment out any other issues with conflicting data types, I made my third attempt to implement models.  As it turns out, blindly ignoring problems with the code greatly improves the rate at which I can write said code, and I finished my work in 12:14.30.  This was then increased to 13:00.75 after a second run of CheckStyle revealed a couple of unused import statements.  The fully functional model-2 branch is available at <https://github.com/bsogata/digits/tree/model-2>.

## Adding CRUD Functionality
Finally, with the <code>Contact</code> model implemented I continued on to implement the ability to update fields.  In order to keep track of the specific <code>Contact</code> being updated, I added an ID field to the <code>Contact</code> model; this ID was then passed to the New Contact view, which would then double as an Edit Contact view for convenience.  An ID of 0 would indicate that the New Contact page should create a new contact, while any other (valid) number would be equal to the ID of the Contact to modify.  This was comparatively easy after the struggles with the <code>Contact</code> model, and it took 22:58.39 to initially finish the crud-1 branch at <https://github.com/bsogata/digits/tree/69e63cd6cbfa20b9fce4e31c1044ed733c2f97e4>.

However, there were a couple of minor problems with this code, where "minor" is the mean value between "insignificant" and "absolutely disastrous".  I neglected to add a JavaDoc tag for the ID field being passed to the New Contact view; though clearly undesirable from a coding standards perspective, it did not impair the performance of the program and following all of the other coding standards meant that the code should have been fairly self-documenting (one would assume that other developers would guess that the variable named <code>id</code> refers to the ID field rather than the psychodynamic term).  Unfortunately, my other mistake was not noticing that "editing" a contact actually created a new contact alongside the original.  Both of these were discovered through a code review of sorts and were fixed soon thereafter, with the final code available at <https://github.com/bsogata/digits/tree/crud-1>.

## Conclusion
I am very good at making Play not work.  In hindsight, trying to learn how to use Play in two weeks was overambitious, and it is questionable whether I actually know how to use Play: certainly I can create applications that work, but my understanding of how Play actually works is quite limited, and as a result when something goes wrong I have no idea how to address the issue.  It feels very much like I am wholly dependent on external resources to implement new features in Play, recognizing what I am supposed to do based on environmental cues rather than recalling them on my own.  Furthermore, there may be a certain degree of mental fatigue at this point; not noticing that the Edit functionality – basically, the entire point of making the CRUD branch – did not work properly is quite frankly inexcusable and should not have happened.  

Because of this, I will be taking a break of sorts from further exploring new tools and technologies.  Instead, I will continue to focus on Play, practicing and developing my skill within the framework until I am competent enough to avoid mistakes like those above in the future.