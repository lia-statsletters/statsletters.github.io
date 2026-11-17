---
title: "Useful rules of thumb for bounding random variables (Part 2)"
date: 2016-01-15
categories: 
  - "archives"
---

In the previous post  we looked at Chebyshev's, Markov's and Chernoff's expressions for bounding (under certain conditions) the divergence of a random variable from its expectation. Particularly, we saw that the Chernoff bound was a tighter bound for the expectation, as long as your random variable was modeled as sum of independent Poisson trials. In this post, we will expand to the cases in which our random variables **cannot** be modeled as sums of independent random variables (or in the case in which we do not know if they are independent or not, or even their distribution). For that, this post will be on two inequalities involving Martingales: Kolmogorov-Doob and Azuma.

Martingales have attracted more than one, especially those related to gambling (for some anecdotal cases, check [here](http://www.jehps.net/juin2009/Mansuy.pdf)). The martingales we refer to in this post, are _sequences_ of random variables. So, for a sequence X\_0, X\_1,... if for all i>0:

E\[X\_i | X\_0,...,X\_{i-1}\] = X\_{i-1}

And this is known as a _martingale sequence_. Consequently, in _martingale sequences_, E\[X\_i\] = E\[X\_0\] for all i≥0. Taking of X\_i as the capital of a gambler playing _a fair game_ after the ith bet. In a fair game, both players have the same chance of winning, so the expected gain or loss from each bet is zero. So even if sometimes you win and sometimes you lose, gains and losses should cancel each other and converge at the initial value. Hence the phrase "quit while you are ahead".

When we get a sequence with the following property:

E\[X\_i |X\_0,..., X\_{i-1}\] ≥ X\_{i-1}

then the expected value of our capital would either remain or grow with each bet. It doesn't mean we will never lose, it only means that time is in our side. And such sequences are known (unsurprisingly) as _super-martingales_.

The concept becomes even more appealing to gamblers when we define martingales in terms of net gains or losses from  the ith bet. So, being Y\_i=X\_i-X\_{i-1} (or the difference between the capital of the gambler in bet i and in bet i-1) and X\_i = X\_0 + ∑Yj (from j=1 until j=i), we can get something called a sequence of differences (also named _martingale differences_). In martingale differences, it holds that for all i≥1:

E\[Y\_i | Y\_1,...,Y\_{i-1}\] = 0

There is a way to construct martingale sequences from any random variable (also known as Doob martingales). It is also possible to convert super-martingales into martingales. But maybe that is a matter to talk about in another post. Maybe titled "Martingales are awesome".

Now, lets get into the matter of our expectation bounds. Now, how would a person deciding where to invest its capital feel if he/she could have an idea of when to "pull out" of the investment (a.k.a the time i of expected maximum capital during the cycle). Or if he/she has provisioned enough to survive the roughest time of the investment?.

## Kolmogorov-Doob bound:

Let X\_0, X\_1,... be a martingale sequence. Then for any λ > 0 :

Pr\[max\_{0≤i≤n} X\_i ≥ λ\] ≤ E\[|X\_n|\] / λ

This form of Kolmogorov-Doob tells us that for a capital X, the probability of having maximum capital ≥ λ in any bet i of the whole game (a.k.a. that moment in which you are on fire) is bounded by E\[|X\_n|\]/λ.

Notice that E\[|X\_n|\] is the sum of the product of all possible positive AND negative values times their probabilities (shamelessly citing wikipedia [here](https://en.wikipedia.org/wiki/Expected_value#General_definition)). Following that, if there was an equal probability of X\_n taking any value between X\_n and -X\_n, then E\[|X\_n|\] would become 0 and supporting myself on |E\[X\]| ≤ E\[|X|\], and being |E\[X\]| non zero if X0 is nonzero, then it must apply that in a martingale, the probabilities of having any specific value of X\_n between X\_n and -X\_n are not the same for every value, unless (possibly) X\_0 was 0 -interestingly, I have not found explicit restrictions over the value of X\_0-. If you wanted to be pessimistic and lazy, you could use |E\[X\_n\]|/ λ = |X\_0|/λ as your bound instead -if the worst case scenario does not look so bad and you have no other information, you may as well dwell with care into it-. You may optionally scream "[YOLO](http://www.urbandictionary.com/define.php?term=Yolo)" for courage.

## Azuma's bound:

Can be found in other textbooks as Hoeffdings's inequality. Let X\_0, X\_1,... be a martingale sequence so that for each for each k:

|X\_k - X\_{k-1}| ≤ _c\_k_

where _c_ is independent of k. Then, for all t≥0 and any λ >0,

Pr\[|X\_t-X\_0| ≥ λ\] ≤ 2e^( (-λ^2) /(2\*∑(c\_k)^2 (for k=1 to k=t) ) )

This bound over martingales resembles the exponential bounds in Chernoff's inequality. It basically tells us that the probability of X deviating more than λ from its initial value in a bet t, is bounded by an exponential function, given that the successive differences in each bet are less than or equal to a certain quantity _c_. The process of applying this bound to a martingale sequence is also known as the method of bounded differences.

To apply any of the former methods you would have to of course do your homework and find out as much information as you can on the system from which the martingale is generated. Sometimes it can be useful to build the martingale from a relaxation of the system, make your calculations over it, and see if your relaxation is harder than how the system is more likely to behave. And there are many other useful bounds over martingales that are not in this post. In other words, if you can possibly model a system's behaviour with martingales, you can get a much better idea of the system without necessarily relying on experimental data (see Polya's urn problem in our next post, "Martingales are Awesome").

 

Most information in this post was taken from section 4 of the [Randomized Algorithms](https://books.google.se/books?id=QKVY4mDivBEC&printsec=frontcover&dq=Motwani+R+randomised&hl=en&sa=X&ved=0ahUKEwjzs_nmyKTJAhXFfw8KHSVwB-cQ6AEIHzAA#v=onepage&q&f=false) book from R. Motwani and P. Raghavan, and from sections 7 and 12 from the [Probability and Random Processes](http://www.scribd.com/doc/200144388/Grimmett-g-r-Stirzaker-d-r-Probability-and-Random-Processes-3ed-Oxford-2001-1#scribd) book from Grimmett and Stirzaker.
