---
title: "Studying random variables with Doob-Martingales"
date: 2016-02-07
categories: 
  - "archives"
coverImage: "martingales.jpg"
---

Or "Martingales are awesome!".

In a previous post, we talked about bounds for the deviation of a random variable from its expectation that built upon Martingales, useful for cases  in which the random variables **cannot** be modeled as sums of independent random variables (or in the case in which we do not know if they are independent or not, or even their distribution). We briefly explained that a martingale sequence is a sequence X\_0, X\_1,… so that for all i>0:

E\[X\_i | X\_0,…,X\_{i-1}\] = X\_{i-1}

and also:

 E\[X\_i\] = E\[X\_0\] for all i≥0.

We discussed two bounds over variation of expectation when we have a Martingale (Azuma and Kolmogorov-Doob). However, the point of treating random variables as Martingales was not touched.

## And, how exactly can I treat any random variable as a Martingale?

[Easy, cowboy](https://www.youtube.com/watch?v=mXX39ChdHvE). Consider a probability space (Ω,**F**,**Pr**), in which **Pr** is a probability measure assigned to a field (Ω,**F**), from which Ω is a sample space, and **F** is a collection of subsets of the sample space Ω. One can see a sample space as an arbitrary set containing all possible outcomes in a probabilistic experiment. Events are subsets of the sample space. For instance, if the experiment is a sequence of two coin-flips, then Ω contains {hh,ht,th,tt}. An event ε ⊆ Ω for the experiment of two coin-flips can be the cases in which we get different values on each coin flip, containing {ht,th}.  The collection of events in **F** must satisfy:

1. ∅ ∈ **F**
2. ε ∈ **F ⇒** complement of ε also ∈ **F** (closure under complement)
3. ε1, ε2,... ∈ **F** **⇒**  ε1 ∪ ε2 ∪ ... ∈ **F** (closure under countable union)

Closure under complement together with closure under countable union also imply closure under countable intersection. For a field in which **F** = 2^Ω, is possible to build sequences of nested subsets of **F** so that **F\_0** ⊆ **F\_1** ⊆ ... ⊆ **F\_n.** From that, we can see that **F\_0** contains the empty event, and **F\_n** contains 2^Ω. Those sequences of nested subsets of **F** is what we call a filter or filtration in the context of probability spaces. Given an arbitrary **F\_i** in a filter, we can say that an event ε ∈ **F** is **F\_i-measurable** when ε ∈ **F\_i.**  This basically means that an event can only be measurable in a filtration, if the subset of the sample space associated to that event is also contained in the filtration. As a consequence of filtration being nested subsets, if an event is **F\_i**\-measurable**,** then the event is also **F\_{i+1}, F\_{i+2},...** and definitely **F\_n** measurable.

Now consider a random variable X over a probability space (Ω,**F**,**Pr**). X can be viewed as a function X: Ω → **R**, meaning that for a given sample ω ∈ Ω, the random variable will take the value X(ω) ∈ **R**. In other words, we have a random variable that is used to associate a random sample in the sample space with a number in the domain of the real numbers. Considering the **F\_i**\-measurability concept, we can say that the random variable X is **F\_i**\-measurable if for each x ∈ **R**, the event {X = x} is contained in **F\_i**. That also means that X is **F\_j** measurable for all j≥i.

Starting from this random variable X, we can build our Martingale. What can be said about X with respect to **F\_{i-1}**? Since X is a function over the values of Ω, we know that the values X will take will be constants over each event. X is a function and its value does not have to be a constant for a sequence of events. It can have a different behavior. However, X is well defined enough to have an expected value over a sequence of events, and such expected value is:

E\[ X | **F\_{i-1}** \]

Which is the expected value of our random variable X over the events contained in **F\_{i-1}.** And this expected value is in itself another random variable. A random variable that constitutes a mapping from **F\_{i-1}** into the reals. An interesting property of this random variable, is that its value is constant if X is also **F\_{i-1}**\-measurable. This means that the expected value of X given **F\_{i-1}** will be constant as long as there are events in **F\_{i-1}** for all values X can take. And of course, there is the case in which E\[ X | ****F\_{i-1}**** \] can be constant if E\[X\] is constant, when X is independent of ****F\_{i-1}**** (since then, from conditional expectation rules, E\[ X | ****F\_{i-1}**** \] will simply be E\[X\]).

Putting everything together: for a probability space (Ω,**F**,**Pr**) with a filtration **F\_0** ⊆ **F\_1** ⊆ ..., and a sequence of random variables X\_0, X\_1, ..., so that for all i≥0, X\_i is **F\_i**\-measurable. Then, the sequence X\_0,... X\_n is a martingale, as long as for all i≥0,

E\[ X\_{i+1} | **F\_i** \] = X\_i

Any subsequence of a martingale is also a martingale, relative to the corresponding subsequence of the filter. Considering that, and knowing that X is a random variable over the probability space, then is possible to define:

> X\_i = E\[ X | **F\_i** \]

and it will follow that the sequence X\_0,... X\_n is also a martingale. This is how you construct a martingale from a random variable, and is also known as a Doob martingale. The key point is that each for each 0≤i≤n, X\_i is **F\_{i-1}**\-measurable.

 

## So, I can treat a random variable as a Martingale. What can I do with that?

[You could do this](https://www.youtube.com/watch?v=-i5y8-U6Mt8). And while you are at it, you can consider the following:

- All martingale properties are applicable to this martingale sequence.
- The expectation variation bounds with martingales discussed in the previous post are applicable. Those are powerful bounds since they are not so restrictive.
- Constructions of martingale differences is possible by having Y\_i = X\_i - X\_{i-1} and requiring E\[Y\_{i+1} | **F\_i**\] =0

But if you want some examples, we can give you some ideas to build a relaxation of your real application.

### Polya's Urn Scheme:

> Consider an urn that initially contains b black balls and w white balls. We perform a sequene of random selections from this urn, where at each step the chosen ball is replaced with c balls of the same colour. Let X\_i denote the fraction of black balls in the urn after the ith trial. Show that the sequence X\_0, X\_1... is a martingale.

To prove this, we will use a property of martigales, by which for all i≥0, E\[X\_i\] = E\[X\_0\], and we will first take the trivial case, and use it to build a general case.

First, let's take the trivial case. The value of X\_o is a constant depending on b and w, which is which is b/(b+w). Since the expected value of a constant is the constant, then E\[X\_o\] = X\_o .

Now, let's build an expression for the general case of X\_i. Since at each trial we replace the chosen ball with c balls of the same colour, then on every ith step we add in total (c-1) balls into the urn. This means that in any given point i, we will have in total:

b+w+i\*(c-1)

balls. X is the fraction of black balls in a given time i, so that numerator becomes itself a random variable depending on the expected value of black balls at point i. Then, we can say that at a certain point i we will add (c-1) black balls with probability E\[X\_{i-1}\]. We use E\[X\_{i-1}\], since the fraction of balls in the urn (X) is a probability, but since the value of such probability is a random variable itself, then we talk expected values of that random variable. In this way, the numerator becomes:

b + expected value of black balls at time i

which is:

b + Σ (number of black balls added on each i) \* (probability of adding a black ball at i)

which for all i>0 is:

b + Σ (from 0 to k=i-1) (c-1) \* E\[X\_k\]

Now putting numerator and denominator together:

E\[Xi\] = (b + Σ (from 0 to k=i-1) (c-1) \* E\[X\_k\]) /  (b+w+i\*(c-1))

This expression holds for i>0. Let us first verify that this expression holds for i=1:

 

E\[X\_1\] = (b + Σ (from 0 to k=0) (c-1) \* E\[X\_0\]) /  (b+w+(c-1))

E\[X\_1\]= (b+ (c-1) \* b/(b+w) ) / (b+w+c-1) = ((b\*(b+w)+b\*(c-1)) / (b+w)) / (b+w+c-1)

\= (b\*(b+w+c-1)) / ((b+w)\*(b+w+c-1)) = b/(b+w)

So, E\[X\_1\] = E\[X\_0\]. For the nth case:

 E\[X\_n\] = b\*(b+w+n\*(c-1)) / (b+w)\*(b+w+n(c-1)) = b/(b+w)

Again, E\[X\_n\] = E\[X\_0\]. Which is what we intended to demonstrate. [Oh yeah](https://vimeo.com/88762546). You can look at other examples for inspiration in 18.2.1 of [here](http://www.cs.berkeley.edu/~sinclair/cs271/n18.pdf), the whole presentation [here](http://www.imada.sdu.dk/~jbj/DM839/FL15.pdf), and something a bit more hardcore yet well explained [here](http://www.math.ucsd.edu/~jverstra/262b-part5.pdf).

Enjoy! [Now that you read the post, you may feel like this video](https://www.youtube.com/watch?v=StTqXEQ2l-Y).

The featured image of the title comes from [here](https://stocksnap.io/photo/BPOUCA7XYU).
