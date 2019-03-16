---
layout: post
title: "Do rebounds really win games?"
date: 2017-02-12
---

If you're a basktball fan you might have heard this popular saying: "Rebounds win games!"

For those non-basketball junkies out there, a rebound is when a player retrieves the ball after someone has just missed a shot. An "offensive rebound" is when your team is on offense and someone on your own team has just missed a shot and a "defensive rebound" is when your team is on defense and someone on the other team has just missed a shot. 

The saying mentioned above about rebounds winning games seems to almost imply that a team should simply focus on getting as many rebounds as possible in order to win games. 
And obviously no coach will be extreme enough to say that that is all a team needs to do to win, but the general idea is still there: Focus on winning the rebound game and your chances are good.

Today I look to explore this question of rebounds in basketball using game log data from the NBA 2015-2016 regular season that I have scraped from [stats.nba.com](//stats.nba.com).

Before we go further, let me explain my theory. There's no doubt that getting rebounds will positively impact your chances of winning a basketball game, but I believe that the main reason why rebounds are often correlated with winning basketball games is because you simply tend to get more rebounds when the opposing team is missing a lot of their shots. And conversely, the opposing team will not get very many rebounds when your team is making most of your shots. 
In other words, maybe the real explanation is that the team that happens to be shooting more accurately tends to also get more rebounds because there are just more opportunities to grab defensive rebounds. And via this explanation, rebounding is simply correlated and not causal to winning games. The real underlying cause is better shooting.

First, let's take a look at a heatmap of the correlations between various stats.

![heatmap](https://github.com/wmoon5/wmoon5.github.io/blob/master/images/rebounding/correlation_heatmap.png?raw=true)

There's too much information on this plot to really go into, but I encourage you to take a look at the various statistics that are strongly correlated with each other and convince yourself why they make sense. Here is a [link](https://github.com/wmoon5/wmoon5.github.io/blob/master/images/rebounding/correlation_heatmap.png?raw=true) to the image to see it full size.

Specifically, I would like to look at which stats are most strongly correlated to the "Plus/Minus" stat, which is just the point differential between the two teams (a positive value indicating that your team won). 

![correlations](https://github.com/wmoon5/wmoon5.github.io/blob/master/images/rebounding/PlusMinus_correlations.png?raw=true)

Here we can see that the statistic most highly correlated with Plus/Minus is the difference in field goal percentage differential (FGPCT_DIFF). In other words, the extent to which a team is shooting more accurately than the opposing team is most highly correlated with the final score difference. However, we can also see that the difference in rebounds (REB_DIFF) between the two teams is also correlated to a relatively high degree. 

In order to answer my question about rebounding, shooting accuracy, and winning, I calculate the [partial correlation](https://en.wikipedia.org/wiki/Partial_correlation) between Plus/Minus and other statistics with the effect of FGPCT_DIFF removed. If the correlation between Plus/Minus and REB_DIFF is really driven solely by FGPCT_DIFF, we would expect the partial correlation decrease close to zero. 

And here are the partial correlation results:

![partial correlations](https://github.com/wmoon5/wmoon5.github.io/blob/master/images/rebounding/PlusMinus_PartialCorrelations.png?raw=true)

As we can see, Plus/Minus and REB_DIFF are still correlated fairly strongly even having filtered out the linear effect from FGPCT_DIFF. Contrastingly, the FG_PCT stat, which was the third most correlated to Plus/Minus earlier now has a partial correlation of close to zero with Plus/Minus. This shows that, once you remove the effect of FGPCT_DIFF, there is not much correlation between FG_PCT and Plus/Minus that remains.

So, what does this all mean? It means that my theory doesn't seem to be correct. Although the correlation between Plus/Minus and REB_DIFF did decrease after removing the effect of FGPCT_DIFF, there still remained an appreciably correlation afterwards. In other words, it does seem like winning the rebounding battle is indeed one of the most important factors in winning a basketball game and it isn't simply a result of shooting better than the other team. 

Therefore, to all you basketball players out there, get after those boards! Here's one of my [favorite pictures](http://i.imgur.com/Sq6esXu.jpg) for inspiration.
