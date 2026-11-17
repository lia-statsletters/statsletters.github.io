---
title: "Useful rules of thumb for bounding random variables (Part 1)"
date: 2015-11-22
categories: 
  - "archives"
  - "life-hacks"
coverImage: "thunder.jpg"
---

 

In a [previous post](https://statsletters.wordpress.com/2015/11/09/book-chapter-review-if-your-model-is-mis-specified-are-you-better-off/) we were discussing the pros and cons of parametric and non-parametric models, and how they can complement each other. In this post, we will add a little more into the story. More specifically, we are going to talk about bounds to the probability that a random variable deviates from its expectation. In these two posts we will talk about the following well-known techniques:

1. Chebyshev's Inequality
2. Markov's Inequality
3. Chernoff's Bounds

They exploit the knowledge on some feature of the random variable e.g. the variance of the distribution, or the random variable being obtained from a poisson process, or knowing that the random variable does not have negative values. You can find extensions for other properties of the random variable under "tail inequalities" or "deviation inequalities". Techniques 1 and 2 were developed in the last part of the 1800's. The latest is a bit more modern (the author [is still alive!](http://www.azquotes.com/quote/702445)).

Why would you want to estimate bounds over the probability that a random variable deviates from its expectation? Some applications rely on expected values to make estimates/predictions.  And on many cases, this is a reasonable assumption to make. If you want to use expected values to represent a random variable, or as part of another technique to provide an output in a decision making process, then is sensible to provide some bounds on the probability that the random variable may deviate from the expectation.

If you are lucky enough to find a problem (or a simplification of a problem) in so that it satisfies all conditions necessary for all techniques, the order of "tightness" of the bounds is Chernoff-Chebyshev-Markov, being Chernoff the tightest. This is possibly the reason why, in spite of Chebyshev's inequality being older, many textbooks choose to talk about Markov´s inequality first. It is not rare to see authors use Markov's inequality in the proof for Chebyshev's. Actually, is not rare at all to see Markov's inequality while going thru proofs, simply because it requires so little from your random variable, so it became a staple in the pantry of statisticians.

## Chebyshev's Inequality

Take-home message: "The probability that a random variable is at least t standard deviations away from its expectation is at most 1/t^2"

Condition: We know the variance of the distribution.

Boring footnote: Some notes use interchangeably the distance from the expectation and the distance from the mean, which for a big enough number of samples becomes reasonable. I chose to use the expectation instead because the demostration of Chebyshev via Markov uses a random variable composed of the absolute value of the difference between your random variable and its expectation, so is easy to remember. But both are probably just as fine.

## Markov's Inequality

Take-home message: "The probability that a random variable takes values bigger than or equal to t times its expectation, is less than or equal to 1/t".

Condition: The random variable must not take negative values.

Boring footnote:  It would make more pedagogical sense to start with Markov's inequality, but I feel I need to start making some historical justice. If I find something older and just as useful as Chebyshev's, I will probably make a newer post and scorn myself. [Like this](http://giphy.com/gifs/no-disapproval-look-of-1Z2I7ScPbWgpO).

Ok, sorry about that link. [Here, have some eyebleach.](http://giphy.com/gifs/barkpost-cute-omg-puppies-XuOOXWY29Y4z6)

## Chernoff's Bounds

Take-home messages:

"The probability that a random variable X built from the sum of independent Poisson Trials deviates to less than (1-δ) times their expectation μ, is less than exp(-μ δ ^2 / 2)"

"For the same random variable X, the probability of X deviating to more than (1-δ) times μ, is less than (exp(δ) / (1+δ)^(1+δ) ) ^ μ.

Conditions: The random variable must be a sum of independent Poisson trials.

This post will hopefully motivate you to study this topic on your own. If you do, some books you can check out:

- [Randomized Algorithms - R. Motwani, P. Raghavan](https://books.google.se/books?id=QKVY4mDivBEC&printsec=frontcover&dq=Motwani+R+randomised&hl=en&sa=X&ved=0ahUKEwjzs_nmyKTJAhXFfw8KHSVwB-cQ6AEIHzAA#v=onepage&q&f=false).
- [Probability and Computing: Randomized Algorithms and Probabilistic Analysis - M. Mitzenmacher and E. Upfal.](https://books.google.se/books?id=0bAYl6d7hvkC&redir_esc=y)

 

The beautiful image for the preview is from [here](https://stocksnap.io/photo/EDL9FU6A9F).
