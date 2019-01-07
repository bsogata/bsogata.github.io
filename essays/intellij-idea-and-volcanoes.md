---
layout: essay
type: essay
title: The Link Between IntelliJ IDEA and Volcanoes
# All dates must be YYYY-MM-DD format!
date: 2015-02-03
labels:
  - Interactive Development Environments
---

(Editor's Note: Older readers may recall the good old days when 8GB RAM was more than enough to comfortably write code.)

One of the disadvantages of living near an active volcano (not quite close enough for the obvious problem of being engulfed in lava) is that breathing in volcanic ash makes it very difficult to think properly.  Normally the proper way to resolve an issue is to address its source, so one might reasonably conclude that I should destroy the volcano or move away.  The first option is computationally expensive while the second course of action is financially expensive, so neither of the solutions are particularly feasible.   However, they serve as an example of a solution that requires some sacrifice in the short-term in exchange for a potential long-term gain<sup>1</sup>.  

Trying to learn how to use a new IDE is similar to my current environment in some respects.  I have referred to my use of [Eclipse](http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/lunasr1a) in other posts here, and Eclipse has served as my IDE of choice for the past few years.  However, I recently had the opportunity to try [IntelliJ IDEA](https://www.jetbrains.com/idea/), another IDE with extensive support for Java and other languages.  Adapting to use IntelliJ IDEA has actually not been all that difficult, though I am certainly not an expert user; nonetheless, making the transition to an entirely new development environment does feel slightly awkward at times.  Unlike dealing with troublesome volcanoes though, the cost of evaluating a new IDE is relatively low.  IntelliJ IDEA does seem a bit slow to start at times – sometimes the IDE starts up in a few seconds, sometimes it takes around a minute – and the first compilation for a project takes a while.  Adjusting to the different key bindings will take some time, and it appears that I cannot use the Alt key to open up menus.  However, these are minor issues for the most part.

To practice using IntelliJ IDEA, I looked at [Project Euler](https://projecteuler.net/) for exercises to work on in Java.  This was done with the same intent as the FizzBuzz exercise when I was learning how to use Eclipse, though with the inclusion of GitHub as well.  I recorded the time that it took me to complete the first three problems for Project Euler, beginning when I started to create a new repository on GitHub and stopping when I made my final commit.  The aforementioned volcanic ash made completing these tasks this rather difficult, but given that I performed somewhat better than I had expected I cannot really use that as an excuse for not doing well.

## Project Euler Problem 1
Problem 1 Description: <https://projecteuler.net/problem=1>

My solution is available at <https://github.com/bsogata/ProjectEulerOne>.  This problem took me 6:45.91 to complete, which is faster than the eight minutes I had been aiming for.  I attribute this to studying the FizzBuzz problem mentioned above, which involves checking if numbers are divisible by three or five; since this problem also required finding multiples of three and five, I may have had a slight advantage in finding a solution.

## Project Euler Problem 2
Problem Description: <https://projecteuler.net/problem=2>

My solution is available at <https://github.com/bsogata/ProjectEulerTwo>.  This problem took me 8:50.76 to complete initially, though this increased to 9:32.72 as I later found a formatting issue in the code and had to correct the formatting error before making another commit into the GitHub repository.  This time was within the acceptable range I had for this problem, between 9 and 12 minutes, and with a few minor improvements I likely would have been able to reach my goal of completing the solution in under 9 minutes.  The only significant programming issue I had was in making the Fibonacci sequence itself.

<pre>
twoBack = oneBack;
oneBack = (oneBack + twoBack);
</pre> 

The code was designed to store elements n-2 and n-1 of the Fibonacci sequence at each iteration of the sequence in order to calculate the value of element n.  However, this mostly served to illustrate two flaws: first, that I am not good at thinking of variable names under time pressure and generally assume that I will have time to refactor the code later on (I did not refactor the code later on); second, that the value of n-2 is modified before it is used to update n-1 and thus the result is invalid.  My final solution uses a temporary variable to store the n-2 value instead, then updates the n-1 value using the temporary variable instead.

<pre>
int temp = twoBack;
twoBack = oneBack;
oneBack = (oneBack + temp);
</pre>

## Project Euler Problem 3
Problem Description: <https://projecteuler.net/problem=3>

My solution is available at <https://github.com/bsogata/ProjectEulerThree>.  This problem took me 12:13.41 to complete, also within the acceptable range that I had for this exercise.  There were a couple of issues in working with the code this time.  The first major difficulty was in having to use <code>long</code> values.  Although I have worked with <code>long</code> values before, the <code>int</code> datatype has almost always been sufficient for my needs.  However, 600851475143 is too large to be stored as an <code>int</code>, and it took a few moments to reacquaint myself with the <code>long</code> datatype.  The other mistake I made had to do with my definition of prime numbers since I instinctively wrote a loop to start checking for divisors of a number at 1; since all integers are divisible by 1, the initial version of the program thought that 1 was the largest prime factor of all numbers.

## Conclusion
In hindsight, I probably should have read the requirements for each problem before trying to set a reasonable timeframe in which to complete the exercise.  Volcanic ash makes it difficult to think rationally.  That aside, I am a little more comfortable with IntelliJ IDEA now, enough to continue using it for the time being.  


1: Do not actually destroy the volcanoes on the Big Island now.  Wait until I am somewhere safe on the mainland first.