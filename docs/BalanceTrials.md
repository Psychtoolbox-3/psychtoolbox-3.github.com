# [BalanceTrials](BalanceTrials)
##### >[Psychtoolbox](Psychtoolbox)>[PsychProbability](PsychProbability)

[BalanceTrials](BalanceTrials) balances a set of factors given the factor levels.  It is  
identical to [BalanceFactors](BalanceFactors) except that the first argument is the number  
of trials desired.  It outputs one or more vectors containing factor  
values for each trial, balanced and, optionally, randomized.  
  
[F1, F2, ...] = [BalanceTrials](BalanceTrials)(NTRIALS, RND, LVL1, LVL2, ...)  
  
[BalanceTrials](BalanceTrials) must be called with three or more input arguments.  The  
first argument, NTRIALS, specifies the number of trials desired.  The  
second argument, RAND, determines whether or not the returned factors  
should be shuffled (non-zero values lead to shuffling).  
  
The remaining input arguments specify the levels for each of a set of  
factors.  Factor levels can be specified as numeric vectors or cell  
arrays (e.g., for category names).  The returned factor lists will be the  
same class as the corresponding levels.  
  
WARNING: If NTRIALS is not a multiple of the product of the number of  
levels, then the actual number of trials generated will be more than  
NTRIALS.  To detect this situation, test whether numel(F1) == NTRIALS.  
  
### EXAMPLES:  
  
 [targetPresent, setSize] = [BalanceTrials](BalanceTrials)(80, 0, 0:1, [3 6 9 12]);  
  
 [target, setSize, dur] = ...  
    [BalanceTrials](BalanceTrials)(72, 1, [0 1], [4 8 12], [0 100 200]);  
  
 [samediff, mask] = ...  
    [BalanceTrials](BalanceTrials)(20, 1, {'same', 'diff'}, {'pattern', 'meta'});  
  
See also: [BalanceFactors](BalanceFactors)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychProbability/BalanceTrials.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychProbability/BalanceTrials.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychProbability/BalanceTrials.m</code>
</div>

