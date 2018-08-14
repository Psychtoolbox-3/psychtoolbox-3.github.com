# [QuestRecompute](QuestRecompute)
##### >[Psychtoolbox](Psychtoolbox)>[Quest](Quest)

q=[QuestRecompute](QuestRecompute)(q [,plotIt=0])  
  
Call this immediately after changing a parameter of the psychometric  
function. [QuestRecompute](QuestRecompute) uses the specified parameters in "q" to  
recompute the psychometric function. It then uses the newly computed  
psychometric function and the history in q.intensity and q.response  
to recompute the pdf. [(QuestRecompute]((QuestRecompute) does nothing if q.updatePdf is  
false.)  
  
[QuestCreate](QuestCreate) saves in struct q the parameters for a Weibull psychometric function:  
p2=delta\*gamma+(1-delta)\*(1-(1-gamma)\*exp(-10.^(beta\*(x-xThreshold))));  
where x represents log10 contrast relative to threshold. The Weibull  
function itself appears only in [QuestRecompute](QuestRecompute), which uses the  
specified parameter values in q to compute a psychometric function  
and store it in q. All the other Quest functions simply use the  
psychometric function stored in "q". [QuestRecompute](QuestRecompute) is called solely  
by [QuestCreate](QuestCreate) and [QuestBetaAnalysis](QuestBetaAnalysis) (and possibly by a few user  
programs). Thus, if you prefer to use a different kind of  
psychometric function, called Foo, you need only create your own  
[QuestCreateFoo](QuestCreateFoo), [QuestRecomputeFoo](QuestRecomputeFoo), and (if you need it)  
[QuestBetaAnalysisFoo](QuestBetaAnalysisFoo), based on [QuestCreate](QuestCreate), [QuestRecompute](QuestRecompute), and  
[QuestBetaAnalysis](QuestBetaAnalysis), and you can use them with the rest of the Quest  
package unchanged. You would only be changing a few lines of code,  
so it would quite easy to do.  
  
"dim" is the number of distinct intensities that the internal tables in q can store,  
e.g. 500. This vector, of length "dim", with increment size "grain",  
will be centered on the initial guess tGuess, i.e.  
tGuess+[-range/2:grain:range/2]. QUEST assumes that intensities outside  
of this interval have zero prior probability, i.e. they are impossible  
values for threshold. The cost of making "dim" too big is some extra  
storage and computation, which are usually negligible. The cost of  
making "dim" too small is that you prejudicially exclude what are  
actually possible values for threshold. Getting out-of-range warnings  
from [QuestUpdate](QuestUpdate) is one possible indication that your stated range is  
too small.  
  
If you set the optional parameter 'plotIt' to 1, the function will plot  
the psychometric function in use.  
  
See [QuestCreate](QuestCreate), [QuestUpdate](QuestUpdate), [QuestQuantile](QuestQuantile), [QuestMean](QuestMean), [QuestMode](QuestMode),  
[QuestSd](QuestSd), and [QuestSimulate](QuestSimulate).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Quest/QuestRecompute.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Quest/QuestRecompute.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Quest/QuestRecompute.m</code>
</div>

