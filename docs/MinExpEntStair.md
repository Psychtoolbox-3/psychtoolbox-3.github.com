# [MinExpEntStair](MinExpEntStair)
##### >[Psychtoolbox](Psychtoolbox)>[PsychStairCase](PsychStairCase)

Minimum Expected Entropy Staircase  
  
The staircase gives suggestions for which probe value to test next,  
choosing the probe that will provide the most information (based on the  
principle of minimum entropy = maximally unambiguous probability  
distribution). Probes are chosen from a set of possible probe values  
provided at staircase init, and their use is evaluated based on the  
expected amount of information gain given a space of PSE and slope values  
to test over.  
  
See [MinExpEntStairDemo](MinExpEntStairDemo) for an example and the comments in the method  
functions below for use of the different staircase methods.  
  
By default, a psychometric function ranging from 0% to 100% is used, as  
is suitable for discrimination experiments with a standard in the middle  
of the possible stimulus parameter range. For other paradigms, such as  
n-AFC detection tasks, one can set the guessrate input during staircase  
init to 1/num\_alternatives, e.g. .5 when doing a 2IFC detection task.  
This guess rate is thus not the rate at which participants guess instead  
of do your task (thats the lapse rate), it the minimum rate of correct  
responses as determined by your design. NB: below discussion is based on  
the default psychometric function with the full range, but all points are  
equally valid for a scaled psychometric function.  
  
It is recommended to have the staircase determine the optimal next probe  
based on only a random subset of the response history (see the  
'toggle\_use\_resp\_subset' and 'toggle\_use\_resp\_subset\_prop' methods). This  
makes its operation more robust for response errors and also avoids probe  
oscillations when the fit estimate is converging.  
When we are close to convergence, probes will tend to be near the 25% and  
75% points. If a probe is 25% and you answer '1' (pedestal faster, which  
is likely, because it's near the correct 25% point), then for the next  
trial the peak in expected entropy reduction will generally be the 75%  
point, and vice versa. This can lead to undesirable probe sequences where  
the correct response alternates 0,1,0,1,0,1. If you choose a random  
subset, this will completely eliminate the problem. If the staircase has  
converged to where there are two almost equal expected entropy minima,  
then small variations due to the selection of subsets will randomly vary  
which minimum emerges as lowest.  
This strategy does not significantly affect optimal operation of the  
staircase. Lots of probe values provide useful information. Therefore, it  
is not crucial to have a highly accurate estimate of likelihoods, so  
relatively few trials are sufficient (less than are needed to for final  
estimates of PSE and DL). Throwing out trials for the staircase  
computation yields robustness without much cost.  
  
Another option would be to load a non-uniform prior on the space of  
possible location/mean/PSE and dispersion/slope parameters (known as mu  
and sigma respectively for a cumulative Gaussian - see the loadprior  
method). Probe sampling will then stay reasonable in early trials even if  
there were a couple bad responses. But this strategy is not as robust as  
using a random subset -- bad trials will continue to have an effect  
throughout.  
  
In absence of anything to base the optimal probe value on, the first  
probe is chosen randomly from the set of possible probes. When a prior  
was loaded, a likelihood distribution is available based on which the  
optional probe value can be computed. If for any other reason choosing  
the next probe based on the measure of minimum expected entropy fails,  
the staircase will fall back on the same random probe sampling strategy.  
There is an option to set the first probe value to be tested (see the  
set\_first\_value method), which, for the first trial only, will overrule  
both of the above probe choice strategies. This can be useful if you want  
to be sure that the first trial is an easy one so the participant knows  
what to expect.  
  
Another measure for robustness is to choose a small lapse rate. If lapse  
would be zero and a response error is made by the observer, immediately a  
whole range of mean-slope combinations becomes impossible. If lapse rate  
is non-zero, these would still have a non-zero probability and the  
staircase can rebound. Therefore a lapse rate of 5% or even more  
depending on task difficulty is always recommended. NB: in the default  
discrimination setup of the staircase (guessrate is not specified or set  
to 0), half of the lapse rate is taken off the bottom of the psychometric  
function and half is taken off the top. So if the lapse rate is 0.05, the  
psychometric function will range from 0.025 to 0.975. In the setup for a  
n-AFC detection experiment when the psychometric function has a lower  
bound of 1/num\_alternatives, the lapse rate is taken off the top. So when  
the guess\_rate is set to .5 (2AFC) and the pase rate is set to .05, the  
psychometric function will range from 0.05 to 0.95.  
Note that the staircase does not support a 0 lapse rate in the first  
place as it works with log-probability and we get in trouble if we would  
take the log of a 0 probability. Any lapse rate lower than 1e-10 will be  
adjusted to 1e-10 upon calling the init method.  
  
If the staircase gets stuck at one of the bounds of the probe set, check  
that the sign of the slope space matches the expected sign of the  
response. E.g., lets look at an experiment in which you are doing 2IFC  
task in which the observer is asked to report which interval contained  
the faster motion. If the observer choses the test over the pedestal  
interval the response is 1, if the observer chosen the pedestal to be  
faster, the response is 0. All slopes in the set would in this case be  
positive as the low end of the probe space (slow speeds) is associated  
with response 0 and the high end with response 1. If we however asked the  
observer to indicate the slower interval, the slopes in our slope set  
would not match the task, and the staircase would get stuck at one of the  
probe bounds. In this case, the lower end of the probe space is  
associated with the response 1 and the higher end with the response  
0--we'd thus have a negative slope for the fitted cumulative probability  
function.  
  
The staircase currently only supports logistic and cumulative Gaussian  
(default) psychometric functions (see the set\_psychometric\_func method),  
but others could easily be implemented. Changes should be needed only to  
the private fit\_a\_point method near the bottom of this mfile, providing  
that the function is characterized by two parameters (which do not  
necessarily have to be PSE and slope, though that is the terminology  
here.  
Should you implement such a function, please do send me your code to  
dcnieho @at@ gmail.com.  
  
The above discussion assumes that response inputs to the process\_resp  
method are either 0 or 1 (see note above about their meaning) though in  
practice anything larger than 0 is treated as 1 and anything lower than  
0, including 0, is treated as 0. the staircase can thus easily be  
integrated with programs that use a 1, -1 response scheme.  
  
For actual offline fitting of your data, you would probably want to use a  
dedicated toolbox such as Prins, N & Kingdom, F. A. A. (2009) Palamedes:  
Matlab routines for analyzing psychophysical data.  
http://www.palamedestoolbox.org. instead of using the function parameters  
or PSE and DL returned from staircase methods get\_fit and get\_PSE\_DL.  
Also note that while the staircase runs far more robust when a small  
lapse rate is assumed, it is common to either fit the psychometric  
function without a lapse rate, or otherwise with the lapse rate as a free  
parameter (possibily varying only over subjects, but not over conditions  
within each subject).  
  
  
References:  
 Based on the Minimum expected entropy staircase method developed by:  
 Saunders JA & Backus BT (2006). Perception of surface slant from  
   oriented textures. Journal of Vision 6(9), article 3  
  
 Discussions of conceptually similar staircases can be found in:  
 Kontsevich LL & Tyler CW (1999). Bayesian adaptive estimation of  
   psychometric slope and threshold. Vision Res 39(16), pp. 2729-37  
 Lesmes LA, Lu ZL, Baek J & Albright TD (2010). Bayesian adaptive  
   estimation of the contrast sensitivity function: The quick CSF method.  
   Journal of Vision 10(3), article 17  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychStairCase/MinExpEntStair.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychStairCase/MinExpEntStair.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychStairCase/MinExpEntStair.m</code>
</div>

