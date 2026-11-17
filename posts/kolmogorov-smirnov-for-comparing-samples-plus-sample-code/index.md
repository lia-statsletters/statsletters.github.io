---
title: "Kolmogorov-Smirnov for comparing samples (plus, sample code!)"
date: 2016-12-26
categories: 
  - "archives"
  - "tutorials"
coverImage: "t3106qpafw.jpg"
---

The Kolmogorov-Smirnov test (KS test) is a test which allows you to compare two univariate, continuous distributions by looking at their CDFs. Such CDFs can both be empirical (two-sample KS) or one of them can be empirical, and the other one built parametrically (one-sample).

> Client: Good Evening.
> 
> Bartender: Good evening. Rough day?
> 
> Client: I should have stayed in bed...
> 
> Bartender: Maybe we have just the right thing for you. How about a Kolmogorov-Smirnov?
> 
> Client: Make it two-sample, please.

The null hypothesis for the one-sample case is that the empirical distribution is drawn from the reference distribution (which is usually parametric). For the two-sample test, the null hypothesis is that the two samples were drawn from the same distribution.

What the actual value of the KS statistic is the highest of all differences between the CDFs in the test. An expression for this statistic is:

$latex K\_n = \\sup\_{x} |(F\_{n}-F) (x)|$ (1)

Sometimes in the literature, it is not uncommon to see it expressed like this:

$latex K\_n = \\sqrt{n} \\sup\_{x} |(F\_{n}-F) (x)|$ (2)

Some of you may have spotted the similarity between this expressions, and the [Glivenko-Cantelli theorem](https://en.wikipedia.org/wiki/Glivenko%E2%80%93Cantelli_theorem) (a.k.a. the fundamental theorem of probability by some people). To refresh it a bit, here is Glivenko-Cantelli for you:

$latex |F\_{n}- F|\_{\\inf} =\\sup\_{x\\in R} |F\_{n}(x)-F(x)| \\rightarrow 0 $ almost surely.

And notice the "almost surely". And "almost surely" will have to do. Because this theorem is such a cornerstone of statistics. And other people have made some interesting discoveries around Glivenko-Cantelli. For instance, the [DKW inequality](https://en.wikipedia.org/wiki/Dvoretzky%E2%80%93Kiefer%E2%80%93Wolfowitz_inequality) draws bounds on the convergence of Glivenko-Cantelli by bounding the probability that the $latex F\_{n}$ differs from _$latex F$_ by more than a given constant $latex \\epsilon > 0$ in the reals. This result can be taken to the KS statistic, and we get an estimate for its tail. And then some people start building up even more interesting bounds. For instance, take [this guys](https://arxiv.org/pdf/1107.5356.pdf).

And well, if you simply want to start playing with the KS statistic, there is a short code snippet in [our notebook](https://github.com/lia-statsletters/notebooks/blob/master/Examples_of_things_in_python.ipynb) that you can use to start comparing samples to each other and samples to DF contained in the stats package of scipy.

Enjoy!

The featured image was taken from [here](https://stocksnap.io/photo/T3106QPAFW).
