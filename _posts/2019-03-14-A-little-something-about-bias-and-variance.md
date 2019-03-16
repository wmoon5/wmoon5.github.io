---
layout: post
title: "A little something about bias and variance"
mathjax: true
date: 2019-03-14
categories: [statistics, ML]
---

In my experience, the most common interview topic brought up during data science and machine learning interviews is the famous **"bias-variance trade-off."** Let's dive right in.

The main idea is that there is some underlying **true** model $$f(X)​$$ that accepts a set of inputs $$X​$$ and predicts some output $$Y​$$. For example the $$Y​$$ could be the sale price of a home and the inputs $$X​$$ could be features of the home, such as number of bedrooms and square footage. However, even two identical homes may end up selling for different prices due to randomness that can't be modeled, so we include an error term $$\epsilon​$$ to create our initial starting equation:


$$
Y = f(X) + \epsilon
$$


We then take a training dataset of $m​$ samples and train a model $$g(X)$$ in order to estimate the true model $$f(X)​$$ as well as possible. Thus, a useful metric to keep track of is the expected squared error of trained model for a specific given input $$X=x​$$.

 
$$
E[(Y-g)^2]
$$


A question that came to mind when I saw this equation was: **what distribution is this expectation taken over?** The answer is that the expectation is taken over the distribution of all random training datasets. If we train the same model over different randomly sampled training datasets, we would probably get a different squared error each time. In other words, there is some distribution of squared errors and we care about the expected value or average of this distribution.

Next we'll do some algebra. For brevity we shorten $$f(x)​$$ and $$g(x)$$ as simply $$f​$$ and $$g​$$:


$$
\begin{aligned}
E[(Y-g)^2] &= E[(Y-f+f-g)^2] \\
&= E[(Y-f)^2 + (f-g)^2 + ((Y-f)(f-g))] \\
&= E[(Y-f)^2] + E[(f-g)^2] + E[(Y-f)(f-g)] \\
&= \textrm{Irreducible Error} + E[(f-g)^2] + \textrm{Stuff that equals zero given a couple assumptions}
\end{aligned}
$$


Perhaps it's instructive to pause for a second and go through some terms


$$
\textrm{Irreducible Error} = E[(Y-f)^2] = E[\epsilon^2]
$$


The irreducible error is the term that comes from the intrinsic error that not even the true model $$f​$$ knows how to predict. Notice that this term does not depend on our trained model $$g$$ and thus, there is not much we can do to minimize this. Hence the "irreducible" description.


$$
\textrm{Stuff that equals zero given a couple assumptions} = E[(Y-f)(f-g)]
$$


This term equals zero when we make a couple assumptions about the error term $$\epsilon​$$. First, we must assume that $$\epsilon​$$ has an expected value of zero. Second, we must assume that $$\epsilon​$$ is independent of the trained model $$g$$. 


$$
\begin{aligned}
E[(f-g)^2] &=  E[f^2 - 2fg + g^2] \\
&= f^2 - 2fE[g] + E[g^2] \\
&= (f^2 + E[g]^2 - 2fE[g]) + (E[g^2] - E[g]^2) \\
&= E[f-E[g]]^2 + E[(g-E[g])^2] \\
&= \textrm{Bias}^2 + \textrm{Variance}
\end{aligned}
$$


We can interpret this term has the expected squared difference between the true model $$f​$$ and the trained model $$g​$$ and as we can see, it's precisely from this term that we get our bias and variance terms. 

We can see that $$\textrm{Bias} = E[f-E[g]]​$$. In words, we can interpret the bias as the expected difference between the true model's prediction and the expected (or average) prediction of the trained model. Recall we wrote $$f​$$ and $$g​$$ as shorthand for $$f(x)​$$ and $$g(x)​$$ where $$x​$$ is a single sample we are trying to predict $$Y​$$ for. And recall that the value of $$g(x)​$$ will be different for different randomly sampled training datasets, ultimately creating a distribution of predicted values. The bias is then just the expected difference between the average value of the distribution of predicted values $$E[g(x)]​$$ and the model's predicted value $$f(x)​$$. In other words, the bias tells us how closely our trained model matches up with the true model on average.

We can also see that $$\textrm{Variance} = E[(g - E[g])^2]$$. This variance term is where I most often see people give wishy washy answers online regarding what it actually is. From the equation we can see that the variance is the expected squared difference between a particular predicted value of the trained model $$g(x)$$ and the expected/average value of the distribution of predicted values $$E[g(x)]$$. In other words, the variance tells us how much our trained model's prediction $$g(x)$$ fluctuates depending on different randomly sampled training datasets. 

To make things concrete, let's return to our example of predicting the sale price of a home. A model with a **high bias and low variance** will be *expected* to have a large difference between our model's prediction and the true value on average, but at least the predictions themselves won't change much when we retrain our model multiple times on different datasets. In contrast, a model with **low bias and high variance** will be *expected* to have a similar output as the true underlying model, but the predictions themselves will change a lot if we retrain our model on different datasets. 

Well, that was all a bit dense and technical, but at least we can now make a more precise statement about the bias variance tradeoff! 

**If we assume an independent irreduceable error with mean equal to zero, we can decompose the expected squared error between a trained model's prediction and the true value as the sum of an irreducible error, a bias term quantifying the expected difference between the trained model's prediction and the true underlying model's prediction, and a variance term quantifying how much the trained model's predictions fluctuate based on the randomness from randomly sampling training datasets**.

