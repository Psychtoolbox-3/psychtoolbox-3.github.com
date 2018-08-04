# [QuestDemo](QuestDemo)
##### >[Psychtoolbox](Psychtoolbox)>[Quest](Quest)

[QuestDemo](QuestDemo).m  
  
One of the great contributions of psychophysics to psychology is the  
notion of measuring threshold, i.e. the signal strength required for a  
criterion level of response by the observer (Pelli & Farell, 1994;  
Farell & Pelli, 1999). Watson and Pelli (1983) described a maximum  
likelihood procedure, which they called QUEST, for estimating threshold.  
The Quest toolbox in the Psychtoolbox is a set of MATLAB functions  
that implement all the original QUEST functions, plus several others.  
You can think of it as a Bayesian toolbox for testing observers and  
estimating their thresholds. This QUEST toolbox is self-contained,  
and runs on any computer with MATLAB 5 or better.  
web http://psychtoolbox.org/  
web http://psych.nyu.edu/pelli/software.html\#quest  
  
By commenting and uncommenting five lines below, you can use this file  
to implement three QUEST-related procedures for measuring threshold.  
  
[QuestMode](QuestMode): In the original algorithm of Watson & Pelli (1983), each  
trial is at the MODE of the posterior pdf. Their final estimate is  
maximum likelihood, which is the MODE of the posterior pdf after  
dividing out the prior pdf. (Subsequent experience has shown that it's  
better not to divide out the prior, simply using MODE of posterior pdf  
throughout.)  
  
[QuestMean](QuestMean): In the improved algorithm of King-Smith et al. (1994), each  
trial and the final estimate are at the MEAN of the posterior pdf.  
  
[QuestQuantile](QuestQuantile) & [QuestMean](QuestMean): In the ideal algorithm of Pelli (1987), each  
trial is at the best QUANTILE, and the final estimate is at the MEAN of  
the posterior pdf.  
  
You begin by calling [QuestCreate](QuestCreate), telling Quest what is your prior  
knowledge, i.e. a guess and associated sd for threshold. Then you run  
some number of trials, typically 40. For each trial you ask Quest to  
recommend a test intensity. Then you actually test the observer at some  
intensity, not necessarily what Quest recommended, and then you call  
[QuestUpdate](QuestUpdate) to report to Quest the actual intensity used and whether the  
observer got it right. Quest saves this information in your Quest struct,  
which we usually call "q". This cycle is repeated for each trial. Finally,  
at the end, when you're done, you ask Quest to provide a final threshold  
estimate, usually the mean and sd (of the posterior pdf).  
  
It is important to realize that Quest is merely a friendly adviser,  
cataloging your data in your q structure, and making statistical  
analyses of it, but never giving you orders. You're still in charge. On  
each trial, you ask Quest (by calling [QuestMode](QuestMode), or [QuestMean](QuestMean), or  
[QuestQuantile)](QuestQuantile)) to suggest the best intensity for the next trial. Taking  
that as advice, in your experiment you should then select the intensity  
yourself for the next trial, taking into account the limitations of your  
equipment and experiment. Typically you'll impose a maximum and a  
minimum, but your equipment may also restrict you to particular discrete  
values, and you might have some reason for not repeating a value.  
Typically you'll choose the available intensity closest to what Quest  
recommended. In some cases the process of producing the stimulus is so  
involved that the exact stimulus intensity is known only after it's been  
shown. Having run the trial, you then report the new datum,  
the actual intensity tested and the observer's response, asking Quest to  
add it to the database in q.  
  
To use Quest you must provide an estimated value for beta. Beta  
controls the steepness of the Weibull function. Many vision studies use  
Michelson contrast to control the visibility of the stimulus. It turns  
out that psychometric functions for 2afc detection as a function of  
contrast have a beta of roughly 3 for a remarkably wide range of targets  
and conditions (Nachmias, 1981). However, you may want to estimate beta  
for the particular conditions of your experiment. [QuestBetaAnalysis](QuestBetaAnalysis) is  
provided for that purpose, but please think of it as a limited optional  
feature. It allows only two free parameters, threshold and beta. You may  
prefer to use a general-purpose maximum likelihood fitting program to  
allow more degrees of freedom in fitting a Weibull function to your  
psychometric data. However, once you've done that it's likely that  
you'll settle on fixed values for all but threshold and use Quest to  
estimate that.  
  
Note that data collected to estimate threshold usually are not  
good for estimating beta. The psychometric function is sigmoidal, with a  
flat floor, a rise, and a flat ceiling. To estimate threshold you want  
all your trials near the steepest (roughly speaking) part of the rise.  
To estimate beta, the steepness of the rise, you want to have most of  
your trials at the corners, where the rise begins and where it ends. The  
usual way to achieve this is to first estimate threshold and then to  
collect a large number of trials (e.g. 100) at each of several  
intensities chosen to span the domain of the rise. These data can  
be plotted, making a nice graph of the psychometric function and  
they can be fed to [QuestBetaAnalysis](QuestBetaAnalysis), to estimate threshold and beta.  
  
References  
  
Farell, B., & Pelli, D. G. (1999). Psychophysical methods, or how to  
measure threshold, and why. In J. G. Robson & R. H. S. Carpenter (Eds.),  
A Practical Guide to Vision Research (pp. 129-136). New York: Oxford  
University Press.  
  
King-Smith, P. E., Grigsby, S. S., Vingrys, A. J., Benes, S. C., and  
Supowit, A. (1994) Efficient and unbiased modifications of the QUEST  
threshold method: theory, simulations, experimental evaluation and  
practical implementation. Vision Res, 34 (7), 885-912.  
  
Nachmias, J. (1981). On the psychometric function for contrast detection.  
Vision Res, 21(2), 215-223.  
  
Pelli, D. G. (1987) The ideal psychometric procedure. Investigative  
Ophthalmology & Visual Science, 28 (Suppl), 366.  
  
Pelli, D. G., & Farell, B. (1994). Psychophysical methods. In M. Bass,  
E. W. Van Stryland, D. R. Williams & W. L. Wolfe (Eds.), Handbook of  
Optics, 2nd ed. (Vol. I, pp. 29.21-29.13). New York: [McGraw](McGraw)-Hill.  
  
Watson, A. B. and Pelli, D. G. (1983) QUEST: a Bayesian adaptive  
psychometric method. Percept Psychophys, 33 (2), 113-20.  
  
All the papers of which I'm an author can be downloaded as PDF files  
from my web site:  
web http://psych.nyu.edu/pelli/  
  
Try "help Quest".  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Quest/QuestDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Quest/QuestDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Quest/QuestDemo.m</code>
</div>

