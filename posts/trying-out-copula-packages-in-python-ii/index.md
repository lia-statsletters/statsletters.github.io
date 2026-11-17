---
title: "Trying out Copula packages in Python - II"
date: 2016-11-16
categories: 
  - "archives"
  - "tutorials"
tags: 
  - "copula"
  - "copulas"
  - "notebook"
  - "python"
  - "python-package"
  - "statistics"
  - "statsmodels"
coverImage: "frechetbounds.png"
---

And here we go with the copula package in (the sandbox of) statsmodels! You can look at the code first [here](https://github.com/statsmodels/statsmodels/blob/master/statsmodels/sandbox/distributions/copula.py).

I am in love with this package. I was in love with statsmodels already, but this tiny little copula package has everything one can hope for!

\[caption id="attachment\_2743" align="aligncenter" width="220"\]![suddenly the world seems such a perfect place](images/tumblr_lu92a7sdsm1qbz8aro5_r2_250.gif) Summarizing my feelings about this package\[/caption\]

## First Impressions

First I was not sure about it. It looks deceptively raw, so one can understand why it would not be fair to compare this with other packages in statsmodels. After googling for examples, none could be found. Not even in the documentation of statsmodels. In fact, to find that this piece of code even existed you had to dig deep.

There are no built-in methods to calculate the parameters of the archimedean copulas, and no methods for elliptic copulas (they are not implemented). However, elliptic copulas are quite vanilla and you can implement the methods yourself. We missed the convenience of selecting a method for transforming your data into uniform marginals, but you can also implement that yourself. You could either choose to fit some parameters to a scipy distribution and then use the CDF method of that function over some samples, or work with an empirical CDF. Both methods are implemented in our notebook.

So in order to actually use the functions in this package, you have to write your own code for getting parameters for your archimedean (we borrowed some code from the copulalib package for that purpose), for transforming your variables into uniform marginal, and for actually doing anything with the copula. However as it is, is quite flexible. Is good that the developers decided to keep it anyway.

## Hands on!

Allright, [check out our notebook at github](https://github.com/lia-statsletters/notebooks/blob/master/Copula%20packages%20continuation.ipynb).
