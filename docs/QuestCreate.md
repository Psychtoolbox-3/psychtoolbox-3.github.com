# [QuestCreate](QuestCreate)
##### >[Psychtoolbox](Psychtoolbox)>[Quest](Quest)

 q=[QuestCreate](QuestCreate)(tGuess,tGuessSd,pThreshold,beta,delta,gamma,[grain],[range],[plotIt])  
  
 Create a struct q with all the information necessary to measure  
 threshold. Threshold "t" is measured on an abstract "intensity"  
 scale, which usually corresponds to log10 contrast.  
  
 [QuestCreate](QuestCreate) saves in struct q the parameters for a Weibull psychometric function:  
 p2=delta\*gamma+(1-delta)\*(1-(1-gamma)\*exp(-10.^(beta\*(x-xThreshold))));  
 where x represents log10 contrast relative to threshold. The Weibull  
 function itself appears only in [QuestRecompute](QuestRecompute), which uses the  
 specified parameter values in q to compute a psychometric function  
 and store it in q. All the other [Quest](Quest) functions simply use the  
 psychometric function stored in "q". [QuestRecompute](QuestRecompute) is called solely  
 by [QuestCreate](QuestCreate) and [QuestBetaAnalysis](QuestBetaAnalysis) (and possibly by a few user  
 programs). Thus, if you prefer to use a different kind of  
 psychometric function, called Foo, you need only create your own  
 [QuestCreateFoo](QuestCreateFoo), [QuestRecomputeFoo](QuestRecomputeFoo), and (if you need it)  
 [QuestBetaAnalysisFoo](QuestBetaAnalysisFoo), based on [QuestCreate](QuestCreate), [QuestRecompute](QuestRecompute), and  
 [QuestBetaAnalysis](QuestBetaAnalysis), and you can use them with the rest of the [Quest](Quest)  
 package unchanged. You would only be changing a few lines of code,  
 so it would quite easy to do.  
  
 Several users of [Quest](Quest) have asked questions on the Psychtoolbox forum  
 about how to restrict themselves to a practical testing range. That is  
 not what tGuessSd and "range" are for; they should be large, e.g. I  
 typically set tGuessSd=3 and range=5 when intensity represents log  
 contrast. If necessary, you should restrict the range yourself, outside  
 of [Quest](Quest). Here, in [QuestCreate](QuestCreate), you tell [Quest](Quest) about your prior beliefs,  
 and you should try to be open-minded, giving [Quest](Quest) a generously large  
 range to consider as possible values of threshold. For each trial you  
 will later ask [Quest](Quest) to suggest a test intensity. It is important to  
 realize that what [Quest](Quest) returns is just what you asked for, a  
 suggestion. You should then test at whatever intensity you like, taking  
 into account both the suggestion and any practical constraints (e.g. a  
 maximum and minimum contrast that you can achieve, and quantization of  
 contrast). After running the trial you should call [QuestUpdate](QuestUpdate) with the  
 contrast that you actually used and the observer's response to add your  
 new datum to the database. Don't restrict "tGuessSd" or "range" by the  
 limitations of what you can display. Keep open the possibility that  
 threshold may lie outside the range of contrasts that you can produce,  
 and let [Quest](Quest) consider all possibilities.  
  
 There is one exception to the above advice of always being generous with  
 tGuessSd. Occasionally we find that we have a working [Quest](Quest)-based  
 program that measures threshold, and we discover that we need to measure  
 the proportion correct at a particular intensity. Instead of writing a  
 new program, or modifying the old one, it is often more convenient to  
 instead reduce tGuessSd to practically zero, e.g. a value like 0.001,  
 which has the effect of restricting all threshold estimates to be  
 practically identical to tGuess, making it easy to run any number of  
 trials at that intensity. Of course, in this case, the final threshold  
 estimate from [Quest](Quest) should be ignored, since it is merely parroting back  
 to you the assertion that threshold is equal to the initial guess  
 "tGuess". What's of interest is the final proportion correct; at the  
 end, call [QuestTrials](QuestTrials) or add an FPRINTF statement to report it.  
  
 tGuess is your prior threshold estimate.  
 tGuessSd is the standard deviation you assign to that guess. Be generous.   
 pThreshold is your threshold criterion expressed as probability of   
    response==1. An intensity offset is introduced into the psychometric   
    function so that threshold (i.e. the midpoint of the table) yields   
    pThreshold.  
 beta, delta, and gamma are the parameters of a Weibull psychometric function.  
 beta controls the steepness of the psychometric function. Typically 3.5.  
 delta is the fraction of trials on which the observer presses blindly.   
    Typically 0.01.  
 gamma is the fraction of trials that will generate response 1 when   
    intensity==-inf.  
 grain is the quantization (step size) of the internal table. E.g. 0.01.  
 range is the intensity difference between the largest and smallest  
    intensity that the internal table can store. E.g. 5. This interval will  
    be centered on the initial guess tGuess, i.e.  
    tGuess+(-range/2:grain:range/2). "range" is used only momentarily here,  
    to determine "dim", which is retained in the quest struct. "dim" is the  
    number of distinct intensities that the internal table can store, e.g.  
    500. QUEST assumes that intensities outside of this interval have zero  
    prior probability, i.e. they are impossible values for threshold. The  
    cost of making "range" too big is some extra storage and computation,  
    which are usually negligible. The cost of making "range" too small is  
    that you prejudicially exclude what are actually possible values for  
    threshold. Getting out-of-range warnings from [QuestUpdate](QuestUpdate) is one  
    possible indication that your stated range is too small.  
  
 See [Quest](Quest).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Quest/QuestCreate.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Quest/QuestCreate.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Quest/QuestCreate.m</code>
</div>

