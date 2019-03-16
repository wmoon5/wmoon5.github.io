---
layout: post
title: "A fun note on Bayes' Rule"
mathjax: true
date: 2019-02-21
---

# Set the scene

An acquaintance (let's call him Bob) comes up to you and asks if you want to grab lunch tomorrow. You wonder to yourself if this is just a friendly platonic lunch or if your acquantaince is romantically interested in you. Let's use Bayes' rule to help us think about this!

To review, Bayes' rule is usually described with the following equation:

$$\begin{equation} \Pr(A \vert B) = \frac{\Pr(B \vert A)\Pr(A)}{\Pr(B)} \end{equation}​$$

First, let's fill in $A​$ and $B​$ with something more concrete:

$$ \begin{equation}\Pr(\textrm{Bob interested} \vert \textrm{Bob asks to lunch}) = \frac{\Pr(\textrm{Bob asks to lunch} \vert \textrm{Bob interested})\Pr(\textrm{Bob interested})}{\Pr(\textrm{Bob asks to lunch})} \end{equation}​$$

# What's it all mean?

Next, we'll go through what each term means. Feel free to skip this section if you don't care too much about the math and want to go to the fun stuff! Wait, but I thought the math *was* the fun stuff...

$$\Pr(\textrm{Bob interested} \vert \textrm{Bob asks to lunch})$$: This is the question we're trying to answer. What is the probability that Bob is interested in you *given the information that he has asked you to lunch*?

$\Pr(\textrm{Bob asks to lunch} \vert \textrm{Bob interested})​$: This is sort of the reverse of the probability above. What is the probability that Bob would've asked you to lunch *given the fact that he is interested in you*? Another way we can interpret this is if, in general, Bob is interested in someone, how likely is he to ask that person to lunch? You can think of this as a general statement about Bob's personality.

$\Pr(\textrm{Bob interested})$: We often refer to this term as a "prior." Basically, it means, before you received the new information (i.e. Bob asking you to lunch), what would you have thought would be the probability that Bob is into you?

$\Pr(\textrm{Bob asks to lunch})$: This term is often a bit more complicated to estimate. This is some general probability that Bob would have asked you to lunch without any knowledge of whether he is into you or not. Sometimes it's easier to rewrite this term as:

$$\begin{equation}\begin{aligned}

\Pr(\textrm{Bob asks to lunch}) = &\Pr(\textrm{Bob asks to lunch}|\textrm{Bob interested})\Pr(\textrm{Bob interested})  \\

&+ \Pr(\textrm{Bob asks to lunch}|\textrm{Bob not interested})\Pr(\textrm{Bob not interested})

\end{aligned}\end{equation}$$



---

# Let's plug in some numbers!

### Scenario 1

$\Pr(\textrm{Bob interested}) = 0.05​$

Maybe we can assume that 1 in 20 guys will be interested in you. That seems a little high actually, but there's nothing wrong with a little optimism.

$\Pr(\textrm{Bob not interested}) = 1 - \Pr(\textrm{Bob interested})  = 0.95​$

For now, let's assume that he's either interested or not interested. None of this silly grey area stuff.

$\Pr(\textrm{Bob asks to lunch} \vert \textrm{Bob interested}) = 0.8$

Bob is a pretty forward guy, so if he's interested in you, he's pretty likely to try and spend time with you by asking you to lunch.

$\Pr(\textrm{Bob asks to lunch} \vert \textrm{Bob not interested}) = 0.4​$

When you think about it a little harder, you remember seeing him going out to lunch with a decent number of platonic friends as well. It's worth noting here that the probability that Bob asks you to lunch when he's not interested in you is still only half compared to when he is interested.

**Plugging in the numbers:**

$$\Pr(\textrm{Bob interested} \vert \textrm{Bob asks to lunch}) = \frac{(0.8 \times 0.05)}{(0.8 \times 0.05) + (0.4 \times 0.95)} = \mathbf{0.095}$$

A 9.5% probability that Bob is interested! So, our previous default guess whether Bob's interested was 5%, but after we've been given the new information that he has asked you to lunch, that probability has increased to 9.5%. The probability increased, but still pretty unlikely he's actually interested.

### Scenario 2

In this scenario let's change one thing: the probability that Bob asks a friend that he's not interested in out to lunch.

$\Pr(\textrm{Bob interested}) = 0.05​$

$\Pr(\textrm{Bob not interested}) = 1 - \Pr(\textrm{Bob interested})  = 0.95$

$\Pr(\textrm{Bob asks to lunch} \vert \textrm{Bob interested}) = 0.8$

$\Pr(\textrm{Bob asks to lunch} \vert \textrm{Bob not interested}) = 0.01​$

In this scenario, you rarely ever see Bob out to lunch with people. He pretty much always eats alone at his desk.

**Plugging in the numbers:**

$$\Pr(\textrm{Bob interested} \vert \textrm{Bob asks to lunch}) = \frac{(0.8 \times 0.05)}{(0.8 \times 0.05) + (0.01 \times 0.95)} = \mathbf{0.808}$$

Wow, 80.8%! That's way different from the result we got previously. But intuitively this makes sense! If it's a relatively normal thing for Bob to ask people out to lunch, regardless of whether he's interested or not, then his asking you to lunch doesn't really say much. However, if it's really out of character for the guy to ask someone out to lunch if he's not interested, then we might start getting suspicious.

### Scenario 3

As a final example, let's see what happens when Bob literally asks *everyone* out to lunch at some point.

$\Pr(\textrm{Bob interested}) = 0.05​$

$\Pr(\textrm{Bob not interested}) = 1 - \Pr(\textrm{Bob interested})  = 0.95​$

$\Pr(\textrm{Bob asks to lunch} \vert \textrm{Bob interested}) = 1.0​$

$\Pr(\textrm{Bob asks to lunch} \vert \textrm{Bob not interested}) = 1.0​$

$$\Pr(\textrm{Bob interested} \vert \textrm{Bob asks to lunch}) = \frac{(1.0 \times 0.05)}{(1.0 \times 0.05) + (1.0 \times 0.95)} = \mathbf{0.05}$$

A 5% probability that Bob is interested! Wait, but that was already your prior probability before he asked you to lunch. Does this make sense?

Yes it does! If Bob really does go to lunch with everyone, then we should get exactly zero information from the fact that he's asked you to lunch regarding the probability that he's interested in you. In other words, there should be no difference between $\Pr(\textrm{Bob interested})$ and $\Pr(\textrm{Bob interested} \vert \textrm{Bob asks to lunch})$. 

# Closing Thoughts

Of course this is a pretty silly and simplistic example, but I do think there are a lot of situations where Bayesian reasoning provides a nice structure to think through problems and situations. How do you think you can apply these concepts to your own life?

Thanks for reading!
