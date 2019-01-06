---
layout: essay
type: essay
title: Testing
# All dates must be YYYY-MM-DD format!
date: 2015-02-17
labels:
  - Software Engineering
  - Testing
---

The JUnit testing framework is commonly used for unit testing in Java, and since testing is a very important component of software engineering getting JUnit to work in IntelliJ IDEA is my next goal.  IntelliJ IDEA has built-in support for JUnit, which makes this a much easier task.  As with the other tools that I have worked with in the past few weeks, I worked on a couple of exercises to familiarize myself with how JUnit works in IntelliJ IDEA, essentially adding tests onto the existing code from [my previous work in learning how to use IntelliJ IDEA](/essays/intellij-idea-and-volcanoes).  The recorded times below started when I created a separate branch to add tests and ended once I had confirmed that the code with tests had been pushed to the appropriate GitHub repository.

## Project Euler Problem 1
My final solution to [the first Project Euler problem](https://projecteuler.net/problem=1) is available at <https://github.com/bsogata/ProjectEulerOne/tree/tests-try2>.  I was aiming for a time of around fifteen minutes to complete this task, and I technically completed the actual testing within twelve minutes the first time through.  However, due to a problem with Git branching (I created the tests-try1 branch properly with <code>git branch tests-try1</code> but did not check out the branch immediately afterward<sup>1</sup>), I had to spend another five minutes trying to restore the master branch of the repository to its original condition while preserving my changes to be put onto the tests-try1 branch.  As a result, my first attempt took a total of 17:02.08 to complete.  This was still within the range that I would consider acceptable for myself under normal circumstances, but since Git had sufficiently annoyed me I decided to repeat the exercise on the tests-try2 branch linked to above.  The second time through took only 11:16.84, well under the targeted time even if one adds a couple of minutes to account for familiarity with the problem.

## Project Euler Problem 2
My solution to [the second Project Euler problem](https://projecteuler.net/problem=2) is available at <https://github.com/bsogata/ProjectEulerTwo/tree/tests-try1>.  My target time here was ten minutes, which in hindsight was overly optimistic.  The biggest problem here was that my original solution to this problem was impossible to test without extensive refactoring, where "extensive refactoring" is defined as "redoing the entire problem."  As it took me just over nine and a half minutes to write the solution to this puzzle in the first place, there was no way that I would be able to rewrite the entire code base and include proper testing in ten minutes.  Consequently, I aborted my first attempt at this after fifteen minutes and spent a few (untimed) minutes writing another solution that would be easier to test.  This also helped to show the need for testing, since my tests failed due to an <code>ArrayOutOfBoundsException</code> when I first ran the tests.

<pre>
  public static int nextFibonacci(List&lt;Integer&gt; numbers) {
    int next = 1;
    
    // If there are not enough numbers to calculate the Fibonacci sequence, add 1 to the list
    if (numbers.size() &lt; 2) { 
      numbers.add(next);
    }
    
    // Else the next number is the sum of the last two elements in the list 
    else {
      numbers.add(numbers.get(numbers.size() - 1) + numbers.get(numbers.size() - 2));
      next = numbers.get(numbers.size() - 1);
    }

    System.out.format("%d + %d == %d%n", numbers.get(numbers.size() - 3), numbers.get(numbers.size() - 2), numbers.get(numbers.size() - 1));

    return next;
  }
</pre>

The <code>System.out.format</code> at the end fails when <code>numbers.size()</code> is less than 3; the intent was to print out the value of each Fibonacci value as it was computed, but of course it is impossible to check numbers that do not exist.  I was able to complete my testing and push the changes to GitHub in 12:28.27 this time.

I am not entirely certain if the tests added accurately verify that the program behaves as expected.  Essentially, <code>tests.ProjectEulerTwoTest.java</code> checks if the <code>nextFibonacci</code> method properly returns values.  While this is a necessary component in solving the second Project Euler problem – which is to find the sum of all even Fibonacci numbers that are less than 4000000 – this does not verify that the sum is performed correctly.  Extracting the generation of Fibonacci numbers was the most intuitive course of action at the time and is still probably the right decision to make, but having other tests to check that the summation is correct would also be good.

## Conclusion
These exercises mostly demonstrate that I am very good at quickly writing code that looks like it should work but falls apart upon further examination.  All of the original code on the master branches behaved as expected; however, the code was written in such a way that refactoring was necessary to make testing possible, and that refactoring process introduced a few defects.  Although being able to finish these exercises within a given time limit is good, writing good code should trump time constraints in all but a few cases (defusing bombs, addressing a cybersecurity threat, finishing homework, etc.).  Consequently, I am not quite certain if my current process of recording how long it takes for me to complete these tasks is really beneficial beyond making sure that I stay on task and helping me to better estimate how long it will actually take me to solve a problem.

Once JUnit is set up in IntelliJ IDEA, it works very nicely.  The need to manually add the JUnit library to the classpath for every new project is somewhat annoying, and the same issue is present for Checkstyle configuration as mentioned previously.  However, as this only takes a minute or so to remedy it is an inconvenience rather than a major problem to be fixed.  Eclipse does have the same problem with JUnit, though it is possible to set the default formatting rules in Eclipse (or at least it is easier to find the settings that allow one to set the default formatting rules; it is entirely possible that I have not located that option in IntelliJ IDEA yet.)

1: The proper solution would have been something like <code>git checkout -b tests-try1</code>.