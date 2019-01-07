---
layout: essay
type: essay
title: slippah
# All dates must be YYYY-MM-DD format!
date: 2019-01-06
labels:
  - slippah
  - Learning by Teaching
---

Traditionally, students attend lectures on campus and work on assignments at home.  The inverted or flipped classroom reverses this model: students listen to lecture videos before class, then work on exercises during class time.  The flipped classroom provides many benefits: students can watch the lectures at their own pace and have both instructors and peers nearby to help them during the in-class exercises, and instructors can better evaluate the progress of their students as they can observe their pupils while they complete their work rather than only seeing the final product.

However, the flipped classroom does depend on students actually learning from the video lectures before class.  Some students may not watch the lectures at all, and those who do may not dedicate their full attention to the video.  If a student does not understand the material before class, then he or she will likely experience difficulties during class due to that deficit in knowledge. 

Administering quizzes synchronized with the lecture videos solves part of the problem.  If students are required to take those quizzes, instructors can at least know whether the students have watched the videos at least once.  However, merely viewing a video in its entirety does not ensure that the viewer learned anything; I have a playlist of videos running in the background as I type this essay and cannot recall anything that happened in any of those videos.

What I have done in conjunction with [Dr. Jan Stelovsky](http://www2.hawaii.edu/~janst/) is to design a system whereby students create quizzes themselves.  In order to create good questions and answers, students must have familiarized themselves with the material.  This uses the concept of learning by teaching, one of the most effective pedagogical methods.

The image below shows the quiz interface.  The lecture video is displayed on the left while the questions and answers for the quiz appear on the right.

<img class="ui image large centered" src="/images/taking_quiz_questions_answers.png">

If the student selects the correct answer, positive feedback appears:

<img class="ui image large centered" src="/images/taking_quiz_correct_answer.png">

If the student selects one of the incorrect answers, negative feedback appears:

<img class="ui image large centered" src="/images/taking_quiz_incorrect_answer.png">

Questions may have hints; these hints may consist of text or links to external resources:

<img class="ui image medium centered" src="/images/taking_quiz_hint.png">

However, our emphasis for educational purposes is on creating the quizzes.  The interface for this is similar to that for taking the quiz, though with significantly more buttons.  

<img class="ui image large centered" src="/images/creating_a_quiz_authoring_tool.png">
<img class="ui image large centered" src="/images/creating_a_quiz_feedback.png">
<img class="ui image large centered" src="/images/creating_a_quiz_hint.png">

Instructors can easily create templates for their students to work on.  Our experiments have divided students into groups (usually comprised of four members per group), so each student only has to create a quiz on a fraction of the lecture video.  Students then take the quizzes from their peers in the group.

<img class="ui image large centered" src="/images/instructor_creating_quizzes.png">

Grading is also straightforward: rather than having to take all of the quizzes one by one (which would be *O(n)*), instructors can look through all of the quizzes that their students created for a particular course.

<img class="ui image large centered" src="/images/instructor_viewing_quizzes.png">

There are of course many areas for improvement in this application.  From the student perspective, taking peer quizzes requires additional time.  Many students have attempted to accelerate the rate of video playback, which currently causes problems with questions not appearing properly: the questions are set to appear at specific times in the video and fast-forwarding through the video may skip over that particular frame.  Although there are APIs that we could use to account for this, it may be simpler to implement a button allowing the quiz taker to skip ahead to the next question in the video.

slippah only supports multiple-choice questions with text answers.  This limits the range of responses for students, and although this makes grading easier answering the questions becomes a matter of recognizing the correct answer rather than recalling the correct answer.  Adding short response or essay questions would require students to think of their own answers rather than selecting or guessing from a list of options.  This might require the quiz authors to grade those questions, giving them an opportunity to view the perspectives of their peers and think about answers that may be correct or incorrect.  Some domains may also be better suited to images for answers.

Students have the option to suggest changes to the quizzes they take.  There is a known bug when the numbers of questions and answers for a particular quiz change: the current system does not properly link questions to the recommended revisions.  Reviewers should also have the capability to suggest adding or removing components rather than merely proposing modifications to existing elements; for example, if the author neglected to write feedback for an answer the student should be able to add that feedback.  There should also be an option to write comments accompanying a suggestion to explain the motivations for the change.

slippah is available at <http://www.slippah.com/>.  Other articles on the theory behind this application include:

* [Applying Augmented Cognition to Flip-Flop Methodology](http://www2.hawaii.edu/~janst/articles/Flip-Flop_Augmented_Cognition.html)
* [Constructive Learning using Flip-Flop Methodology: Learning by Making Quizzes Synchronized with Video Recording of Lectures](http://www2.hawaii.edu/~janst/articles/Flip-Flop.html)
* ["Flip-Flop" Learning by Teaching Methodologies: "Peer Improvement", "Agile Tooltip", Support Technology, and Next Steps](https://link.springer.com/chapter/10.1007/978-3-319-91152-6_30)