# [BuildMarkovK](BuildMarkovK)
##### >[Psychtoolbox](Psychtoolbox)>[PsychProbability](PsychProbability)

K = [BuildMarkovK](BuildMarkovK)(n,r,var)  
K = [BuildMarkovK](BuildMarkovK)(r,var)  
  
Build the covariance matrix for a Markov process as defined in Pratt, pp.  
131 ff.  
  
This routine has two calling forms.  In the first form, three arguments  
are passed and the random variables are assumed to have the save  
variance.  Thus the passed var is a scalar.  
  
In the second form, the passed var is a column vector containing the  
variances of the individual random variables.  
  
8/19/94     dhb     Wrote it.  
2/6/96      dhb     Second calling form.  
7/24/04       awi     Cosmetic.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychProbability/BuildMarkovK.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychProbability/BuildMarkovK.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychProbability/BuildMarkovK.m</code>
</div>

