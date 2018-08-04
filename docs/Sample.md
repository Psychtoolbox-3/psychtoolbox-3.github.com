# [Sample](Sample)
##### >[Psychtoolbox](Psychtoolbox)>[PsychProbability](PsychProbability)

 [Y,index] = [Sample](Sample)(X)  
  
 Returns a random sample from X.  
 If X is a vector, returns a scalar sample from X, so Y = X(index).  
 If X is an m-by-n matrix, m\>1 && n\>1, samples each column of X:  
    for j=1:n, Y(j)=X(index(j),j).  
  
 Also see [RandSample](RandSample), [Shuffle](Shuffle), SORT, and [Randi](Randi).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychProbability/Sample.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychProbability/Sample.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychProbability/Sample.m</code>
</div>

