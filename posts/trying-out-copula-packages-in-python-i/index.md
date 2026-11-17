---
title: "Trying out Copula packages in Python - I"
date: 2016-10-19
categories: 
  - "archives"
  - "tutorials"
tags: 
  - "copula"
  - "copulas"
  - "notebook"
  - "python"
  - "statistics"
coverImage: "copulas.png"
---

You may ask, why copulas? We do not mean this [copulas](https://en.wikipedia.org/wiki/List_of_English_copulae). We mean the mathematical concept. Simply put, copulas are joint distribution functions with uniform marginals. The kicker, is that they allow you to study dependencies separately from marginals. Sometimes you have more information on the marginals than on the joint function of a dataset, and copulas allow you to build "what if" scenarios about the dependency. Copulas can be obtained by fitting a joint distribution to the uniformly distributed margins obtained from the quantile transformation on the cdf of your variable of interest.  For more on them, do check out [chapter 7 of this slides](http://www.qrmtutorial.org/slides).

This post is about Python (with [numpy](http://numpy.org), [scipy](http://scipy.org), [scikit-learn,](http://scikit-learn.org/stable/) [StatsModels](http://statsmodels.sourceforge.net) and other good stuff you can find in [Anaconda](https://www.continuum.io/anaconda-overview)) but R is fantastic for statistics. I repeat: _fan-tas-tic_. If you are serious about working with statistics, it doesn't matter whether you like R or not, you should at least check it out, and see what packages are there to help you. Chances are, someone may have built what you need. And you can work R from python (it needs some setup).

So of course there is [an R package for working with copulas](https://cran.r-project.org/web/packages/copula/index.html) named -with all logic- "copula". The package was built by Marius Hofert, Ivan Kojadinovic, Martin Maechler, and Jun Yan, and maintained by Martin Maechler.

With all of this about how wonderful R is, we are still making a post about how to work with a particular mathematical tool in python. Because as awesome as R is, python does have an incredible flexibility for [otter](https://media.giphy.com/media/tQAApm4PMOpiM/giphy.gif) other matters.

Most of the upcoming content in this post will be built with [Jupyter Notebooks](http://jupyter.org/). I am a recent user and I love them!. StatsLetters will keep some notebooks with python/ R examples in [github](https://github.com/lia-statsletters/notebooks).

### The packages

I was surprised by the fact that there was no explicit implementation of copula packages in scikit-learn (huh?) or scipy (gasp!). However, statsmodels does have an implementation going in their sandbox, which we will try out on a future post:

```
statsmodels.sandbox.distributions.copula
```

The package we will try today is copulalib. Is available in anaconda, and you can pip it. It has a small bug that you can fix yourself, and in the notebook the bug and the small fix are described. I contacted the author of the package, and let him know about this, but I am not sure if the package is still maintained, so I decided to anyway include the bugfix in the notebook.

And with no more introduction, [click here to enjoy our notebook](https://github.com/lia-statsletters/notebooks/blob/master/Copula%20Packages%20Notebook.ipynb)!
