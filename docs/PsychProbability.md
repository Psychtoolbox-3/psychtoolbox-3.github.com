# [PsychProbability](PsychProbability)
##### >[Psychtoolbox](Psychtoolbox)>[PsychProbability](PsychProbability)

Psychtoolbox:[PsychProbability](PsychProbability).  
  
Computation/Evaluation of probability distributions, basic sampling and  
randomization.  
  
  
[BalanceFactors](BalanceFactors)      - Balance a set of factors given the factor levels.  
[BalanceTrials](BalanceTrials)       - Balance a set of factors given the factor levels. Takes alternative parameters wrt. [BalanceFactors](BalanceFactors).  
[BuildMarkovK](BuildMarkovK)        - Build covariance matrix for Markov process.  
[ChiSqrCumulative](ChiSqrCumulative)    - Chi-squared distribution probability function.  
[ChiSquarePDF](ChiSquarePDF)        - Chi-squared distribution PDF.  
[ChooseKFromN](ChooseKFromN)        - Randomly choose k distinct integers out of n.    
[ClockRandSeed](ClockRandSeed)       - Seed rand() and randn() from clock.  
[CoinFlip](CoinFlip)            - Bernoulli random variable.  
[CoinFlipPDF](CoinFlipPDF)         - Bernoulli distribution PDF.  
[ColMean](ColMean)             - Take column means, works for one row matrices.  
[ColStd](ColStd)              - Take column stds, works for one row matrices.  
[CombVec](CombVec)             - Generate all possible combinations of input vectors.  
[CovToCorr](CovToCorr)           - Compute matrix of correlations from covariance.  
[FindNeighborCorr](FindNeighborCorr)    - Find nearest neighbor correlations in data set.  
[MultiNormalDraw](MultiNormalDraw)     - Draw vectors from multivariate normal.  
[MultiNormalPDF](MultiNormalPDF)      - Compute multivariate normal PDF.  
[NormalCumulative](NormalCumulative)    - Univariate normal CDF  
[NormalDraw](NormalDraw)          - Draw from univariate normal.  
[NormalPDF](NormalPDF)           - Univariate normal PDF.  
[NormalProb](NormalProb)          - Compute probability of univariate normal in interval.  
[NRandPerm](NRandPerm)           - Randomly select elements from a random permutation.  
[RandDim](RandDim)             - Randomize matrix along any dimension.  
[Randi](Randi)               - Get random integer sample. Same as [Ranint](Ranint), but Denis prefers it.  
[RandLim](RandLim)             - Generates a matrix of random numbers between a lower and upper limit.  
[RandSample](RandSample)          - Get a random sample from a list.  
[RandSel](RandSel)             - Randomly select elements from matrix, elements are replenished.  
[Ranint](Ranint)              - Get random integer sample. Same as [Randi](Randi), but David prefers it.  
[Sample](Sample)              - Get a random sample from a list.  
[Shuffle](Shuffle)             - Randomly reorder the entries of vector/matrix.  
[UniqueAndN](UniqueAndN)          - Returns unique elements of array and the number of times each element occurs in the array.  
[UniqueNoSorting](UniqueNoSorting)     - Returns elements of array in order of appearance or disappearance.  
[URandSel](URandSel)            - Randomly select elements from matrix, elements are not replenished.  
  
  
Combining [CombVec](CombVec) and [RandDim](RandDim)  
Using [CombVec](CombVec) and [RandDim](RandDim), it is very simple to generate all trials  
in an experiment with a factorial design and then randomize these  
trials:  
  cond\_a = [1 2]; cond\_b = [120 180]; ntrial = 2;  
  trial  = [CombVec](CombVec)(cond\_a,cond\_b);  
  trial  =  
       1     2     1     2  
     120   120   180   180  
  
  trial           = repmat(trial,1,ntrial);   % each combination of conditions occurs ntrial times  
  trial(end+1,:)  = [1:size(trial,2)];        % append trial number  
  trial           = [RandDim](RandDim)(trial,2);         % shuffle trial order  
  
  trial =  
       2     1     1     2     1     1     2     2  
     120   180   180   180   120   120   120   180  
       6     3     7     8     5     1     2     4  
  
  
[BalanceFactors](BalanceFactors).m was contributed by David E. Fencsik (fencsik@gmail.com), thanks!  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychProbability/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychProbability/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychProbability/Contents.m</code>
</div>

{{category}}