---
title: "Joint Distributions"
date: 2019-01-01
categories: 
  - "tutorials"
draft: true
---

On some cases you are studying dependencies between some variables and you happen to have a few thousand samples laying around. If your particular leading questions are on the lines of: "what kind of dependencies can be discarded/uncovered given the information of this samples?", then its time to go [party like is 1959](https://en.wikipedia.org/wiki/1959_in_science). And why 1959? Because that was the year in which Abe Sklar introduced a beautifully simple concept: Turns out, joint CDFs depend on something more than the DFs of their univariate marginals. More specifically, on something that "couples" those marginals together. And that "something" is another function, which Sklar named a copula.

To properly quote Sklar's idea (which is now known as Sklar's Theorem):

Let \[latex\]F\[/latex\] be a joint distribution function with margins \[latex\]F\_1, ..., F\_d \[/latex\]. Then there exists a function (a copula, more specifically) \[latex\]C\[/latex\] such that for all \[latex\]x,...x\_d \\in R\[/latex\]:

\[latex\]F(x\_1,...,x\_d) = C(F\_1(x\_1), ..., F\_d(x\_d))\[/latex\]

If \[latex\]F\_1, ..., F\_d\[/latex\] are continuous, then our function \[latex\]C\[/latex\] is unique; otherwise, \[latex\]C\[/latex\] is uniquely determined on \[latex\]Ran(F\_1) \\times Ran(F\_2) \\times ... \\times Ran(F\_d)\[/latex\].

Conversely, if \[latex\]C\[/latex\] is a copula and \[latex\]F\_1, ..., F\_d\[/latex\] are distribution functions, then the function \[latex\]F\[/latex\] is a joint distribution function with margins \[latex\]F\_1, ..., F\_d\[/latex\].

Now what does this mean? Does this mean that the marginals are not so relevant anymore? Can you just twist them around with something called a copula and build any joint DF? [Is this utopia](https://www.youtube.com/watch?v=OB5Qoy8JHdI)?

Well, not really. To start, not just any function that you pull out of your magic place will be a copula. Copulas can be seen as functions that express dependency on a quantile scale. The value \[latex\]C(u\_1,...u\_d)\[/latex\] is the joint probability that \[latex\]X\_1\[/latex\] lies below its \[latex\]u\_1\[/latex\]-quantile, \[latex\]X\_2\[/latex\] below its \[latex\]u\_2\[/latex\]-quantile, and so on. And there are a few conditions that a function must satisfy in order to accomplish that.

In the references at the end of the post you can find those conditions stated in a more formal manner.

### So, how can a function be a copula?

First, copulas map a d-dimensional unit-hypercube to the unit interval: \[latex\]\[0,1\]^d \\rightarrow \[0,1\] \[/latex\]. And not just any d-dimensional unit hypercube. Copulas specifically map hypercubes is built with standard uniformly distributed marginals (such as those you can obtain from cumulative distribution functions).

Second, copulas are non-decreasing in all d-dimensions. It means that as you go up in the range of the marginals, the value of the copulas can only grow or remain.

If the value of any quantile (point) in any of those d-dimensions is zero, then the corresponding value for the copula is zero as well. A way to make sense of it would be to consider that if the probability of an event is zero, then the probability that event considering anything else would still be zero. And if the value in almost all quantiles in those dimensions is 1 and only in one point is \[latex\]u\[/latex\], then the value of the copula at that point would be \[latex\]u\[/latex\] as well.

As you can see, these properties of the copula create bounds over the values the functions can take, given the values of the marginals. For a more formal statement of these bounds, check out Frechét Bounds.

### Allright. But we still have a lot of room here?

Yes! and no. You see, there are limits for the value that

while each copula-marginals combination will yield a unique joint distribution function, that does not

### I want more!

Using math to get an idea of the world is like gaining another sense. Statistics in particular feels like a sense of smell: use your nose and some leading questions over some data points (hopefully with as much class [as this guy)](https://youtu.be/frRonhQdRdQ?t=68) and that gives you back more questions and sometimes, answers.  

> How can mirrors be real if our eyes aren't real?
> 
> Jaden Smith

<figure>

![](images/2q1amo-1.gif)

<figcaption>

Aristotle's reaction

</figcaption>

</figure>

Hopefully not _those_ questions. But questions such as: Are my products used the way they are intended to be used? How else are my products actually used? How can I better serve my customer given what they use my product for? And if you happen to have a few thousand samples laying around with variables that can reasonably hold information for those answers, then feel free to try some copulas around!

There are other consequences to Sklar's Theorem and Frechet bounds and this is only a blog post after all. If you want a more formal definition, [check out chapter 7 of this book.](https://www.googleadservices.com/pagead/aclk?sa=L&ai=DChcSEwi27ujjjtDfAhXDkhgKHT-7ASIYABAKGgJsZQ&ohost=www.google.com&cid=CAESEeD2J-BM0PmRJXRCoKKM_u2b&sig=AOD64_24p8Qj2HVqgbLfZbF6WxVvssv-tA&ctype=5&q=&ved=0ahUKEwihqd7jjtDfAhWRwosKHe3_B9EQ9aACCKYB&adurl=) Or, you know, [wikipedia](https://en.wikipedia.org/wiki/Copula_\(probability_theory\)#Sklar's_theorem). And if you want a lot more examples and bounds and proofs in detail, check out [chapter 2.3 and 5 of this book](https://g.co/kgs/65imQQ). Or read the whole book, why not. And while you are at that rabbit hole, [go for this](https://en.wikipedia.org/wiki/The_Two_Cultures). Your dinner partner will thank you.
