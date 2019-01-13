# [QuestTest](QuestTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[QuestTest](QuestTest).m  
  
Created by hacking a copy of [QuestDemo](QuestDemo).m, in order to  
do some simulations for Beau Watson.  
  
128 repetitions of each condition  
[Quest](Quest) assumes [LogWeibull](LogWeibull) psychometric function with parameters:  
beta = {1.5, 2., 2.5, 3., 3.5, 4., 4.5, 5., 5.5} (in separate conditions)  
gamma = 0.03  
delta = .01  
sample range = {-30,30} dB  
sample step size 0.5 dB  
Prior is always Gaussian, sd=12 dB, centered on guess.  
Initial guess drawn from Normal distribution with mean 0 and sd=6 dB.  
[Quest](Quest) uses mode of posterior density.  
Simulated observer has [LogWeibull](LogWeibull) psychometric function with parameters:  
{beta=3.5,gamma=.03,delta=.01}  
  
  
By commenting and uncommenting five lines below, you can use  
this file to implement three QUEST-related procedures for measuring  
threshold.  
  
[QuestMode](QuestMode): In the original algorithm of Watson & Pelli (1983)  
each trial and the final estimate are at the MODE of the posterior pdf.  
  
[QuestMean](QuestMean): In the improved algorithm of King-Smith et al. (1994).  
each trial and the final estimate are at the MEAN of the posterior pdf.  
  
[QuestQuantile](QuestQuantile) & [QuestMean](QuestMean): In the ideal algorithm of Pelli (1987)  
each trial is at the best QUANTILE, and the final estimate is at   
the MEAN of the posterior pdf.  
  
King-Smith, P. E., Grigsby, S. S., Vingrys, A. J., Benes, S. C., and Supowit, A.  
(1994) Efficient and unbiased modifications of the QUEST threshold method: theory,   
simulations, experimental evaluation and practical implementation.   
Vision Res, 34 (7), 885-912.  
  
Pelli, D. G. (1987) The ideal psychometric procedure. Investigative Ophthalmology   
& Visual Science, 28 (Suppl), 366.  
  
Watson, A. B. and Pelli, D. G. (1983) QUEST: a Bayesian adaptive psychometric   
method. Percept Psychophys, 33 (2), 113-20.  
  
Copyright (c) 1996-1997 Denis G. Pelli  
  
6/24/97  dgp    wrote it, based on [QuestDemo](QuestDemo).m  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/QuestTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/QuestTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/QuestTest.m</code>
</div>

