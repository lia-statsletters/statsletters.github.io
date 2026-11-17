---
title: "Joint CDFs: Centaurs, Kernels and Fréchet Bounds."
categories: 
  - "blog"
draft: true
---

Today's post is about borrowing a concept from a theoretical framework into another. In the multivariate world you often have a few choices when trying to build a model:

- You go non-parametric and try to fit a bandwidth for a kernel estimator, or the parameters for a mixture model.

- You go parametric and try to fit a copula.

- You do something in between (mixtures, etc)

What you choose could depend on:

Is it possible/reasonable to inject some knowledge of the process that generated your data?

What kind of constraints are "injectable", e.g.:

- Natural modes which you can use to help building a mixture

- Natural dependency behaviours you can use to reasonably choose which copula to fit

- Is it realistic/useful to model small variations in your data, or shall you try to smooth them? Then you can narrow (or widen) your range of choice for a bandwidth in your kernel.

When you know something about the context of your data it should be possible to leverage some of that for building a model.

Or maybe you know nothing about the context of your data. Like that character from a TV series in which there are dragons, zombies, zombie-dragons and naked people. In that case, the usual advice is "may brute-force methods be with you".

## I know nothing, so let's go full Kernels.

With a Kernel estimator one can use a smoothing function to approximate distribution/density functions.

A while ago while reading about [Fréchet bounds](https://en.wikipedia.org/wiki/Copula_\(probability_theory\)#Fr.C3.A9chet.E2.80.93Hoeffding_copula_bounds), a shiny remark ([in section 7.1 of this book](https://www.amazon.co.uk/Quantitative-Risk-Management-Techniques-Princeton/dp/0691166277)) caught my attention. Turns out its possible to bound any multivariate distribution in terms of their own marginals. Fréchet bounds are related to [Fréchet inequalities](https://en.wikipedia.org/wiki/Fr%C3%A9chet_inequalities), which can be considered rules about how to bound calculations involving probabilities without any assumptions of dependence or independence.

And even more interesting, these bounds were pretty uncomplicated to calculate.

For any multivariate DF $latex \\textbf{\\textit{F}}$ with marginals $latex \\textbf{\\textit{F}}\_1,...\\textbf{\\textit{F}}\_d$, the Fréchet bounds are:

$latex max ( \\sum\_{i=1}^{d} {F\_i(x\_i)+1-d},0) \\leq \\textbf{\\textit{F}} ( \\textbf{\\textit{x}} ) \\leq min( \\textbf{\\textit{F}}\_1 (\\textit{x}\_1), ... ,\\textbf{\\textit{F}}\_d (\\textit{x}\_d) ) $

As you see, pretty uncomplicated.

Lets play a bit with Fréchet bounds! [Here is a notebook](https://github.com/lia-statsletters/notebooks/blob/master/Frechet.ipynb) showing how the bounds look like given different combinations of CDFs. You may want to play with the surfaces in the bounds (or wait a week or two for me to find the time to do add that code to the notebook :) ).

Then the motivation for this post came up: Can we use that information of the bounds to build better models? or to build them faster?

> I'm getting heartburn. Tony, do something terrible.
> 
> Snatch **(2000)**

## Fréchet bounds for MV Kernel Estimations.

In Python, one can easily use [Scikit-Learn](https://scikit-learn.org/stable/auto_examples/neighbors/plot_species_kde.html#sphx-glr-auto-examples-neighbors-plot-species-kde-py) or [StatsModels](https://www.statsmodels.org/dev/_modules/statsmodels/nonparametric/kernel_density.html#KDEMultivariate) to get a Kernel **Density** estimation from a multivariate dataset. However only StatsModels has a convenience method to use Kernel estimation to obtain a CDF (as of feb 2019). So we will hack the code and  

## I want more!

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

Hopefully not _those_ questions. But if you happen to have some thousand samples laying around with variables that can reasonably hold information for those answers, then feel free to look into the kind of joint distributions you get.
