# [BalanceFactors](BalanceFactors)
##### >[Psychtoolbox](Psychtoolbox)>[PsychProbability](PsychProbability)

[BalanceFactors](BalanceFactors) balances a set of factors given the factor levels.  It is  
identical to [BalanceTrials](BalanceTrials) except that the first argument in this  
function is the number of replicates per cell.  It outputs one or more  
vectors or cell arrays, each containing factor values for a set of  
trials, balanced and, optionally, randomized.  
  
[F1, F2, ...] = [BalanceFactors](BalanceFactors)(N, RND, LVL1, LVL2, ...)  
  
[BalanceFactors](BalanceFactors) must be called with three or more input arguments.  The  
first argument, N, specifies the number of replicates per combination of  
factor levels.  The second argument, RND, determines whether or not the  
returned factors should be shuffled (non-zero values lead to shuffling).  
  
The remaining input arguments specify the levels for each of a set of  
factors.  Factor levels can be specified as numeric vectors or cell  
arrays (e.g., for category names).  The returned factor lists will be the  
same class as the corresponding levels.  
  
### EXAMPLES:  
  
 [targetPresent, setSize] = [BalanceFactors](BalanceFactors)(2, 0, 0:1, [3 6 9 12]);  
  
 [target, setSize, dur] = ...  
    [BalanceFactors](BalanceFactors)(1, 1, [0 1], [4 8 12], [0 100 200]);  
  
 [samediff, mask] = ...  
    [BalanceFactors](BalanceFactors)(3, 1, {'same', 'diff'}, {'none', 'pattern', 'meta'});  
  
See also: [BalanceTrials](BalanceTrials)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychProbability/BalanceFactors.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychProbability/BalanceFactors.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychProbability/BalanceFactors.m</code>
</div>

