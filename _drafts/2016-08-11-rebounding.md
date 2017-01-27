---
layout: post
title:  "Do rebounds win games?"
date:   2016-08-11 
---

Here's something I've wondered about for a while. 

When it comes to basketball, I always hear coaches and players say things along the lines of *"the team that gets the most rebounds wins"* implying that if you want to win a game, you should really focus on outrebounding the other team. 
And while I certainly don't doubt that poor rebounding will definitely reduce your chances of winning a basketball game, I wonder if there is another way to interpret the observation that it seems like the team with the most rebounds usually wins the game.
If we assume that defensive rebounds are easier to get than offensive rebounds, aren't rebounding numbers largely just a function of the number of missed field goal attempts by the opposing team? And in that case, is the statement about rebounding and winning games just an indirect way of saying the more trivial statement that the team that misses the most shots usually loses?

In other words, if Team A misses more shots than Team B, then Team B will have more opportunities to grab defensive rebounds off those missed shots and thus be more likely to have more rebounds at the end of the game than Team A. In this case it certainly seems like Team B won because they missed fewer shots and not because they got more rebounds. (For the sake of simplicity, we assume in this argument that both teams take the same number of shots in total). It's the classic correlation vs. causation argument.

In statistical terms, I am wondering if rebounding is more of a [confounding](https://en.wikipedia.org/wiki/Confounding) factor than anything else.

I look to explore this question using some data I scraped from the fabulously fun [stats.nba.com](//stats.nba.com). More specifically, I am looking at the game logs for all 1230 games of the 2015-2016 NBA regular season.

First, it's always fun to look at some correlations:

![here is a correlation heatmap](https://github.com/wmoon5/wmoon5.github.io/blob/master/images/kobe/FGPct_ShotZones.eps)

Here is a [link](http://127.0.0.1:4000/images/test.eps) to the correlation heatmap if you'd like to open in a separate tab or window.

Admittedly, there are plenty of interesting correlations in this heatmap (like a strangely large positive correlation between turnovers and rebound differential), but for the purpose of this post, let's try and look more closely at the original claim: *can the positive correlation between rebounding and winning be explained by missed field goals and field goal percentage?*





