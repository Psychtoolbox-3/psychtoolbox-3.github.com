# [MullerLyerIllusion](MullerLyerIllusion)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[PsychExampleExperiments](PsychExampleExperiments)

results = [MullerLyerIllusion](MullerLyerIllusion)(subID)  
  
Presenting the Muller-Lyer Illusion with the Psychtoolbox, complete experiment.  
  
### Input:  
  
  subID = subject Id (scalar), defaults to 66  
  
### Output:  
  
  'results' is a numerical matrix with one row per trial and columns:  
  colHeaders = {'subID', 'trial no', 'trial ID', 'length l1', 'headdir l1',...  
  'length l2', 'headdir l2', 'length ratio', 'correct', 'rt PTB', 'rt ML'}  
  
In this experiment two lines (l1 and l2) are presented, where each line can have   
inward or outward pointing arrow heads at its ends.    
subjects are asked to judge the relative length of the basic lines  
and to respond by pressing 's' for same or 'd' for different  
  
correctness and reaction times are recorded, the latter by two  
different methods in order to compare precision:  
  rt PTB relies on PTB commands which are supposedly more precise  
  rt ML uses the Matlab's native tic/toc stopwatch  
  
This experiment is a counterbalanced 2x2x2x2 design with  
the factors line length (l1, l2) and head direction (l1, l2)  
  The 16 test trials are presented in randomized order, following 3  
randomly drawn training trials  
  The exact design is defined in condtable (see below), where each line  
stands for one trial and the columns for the four factors  
  
line length can be either 1 or 2, these values will be taken as  
indices into the 1 x 2 vector hll (half line length, difference of 10%)  
using indices allows the stimuli to be scaled by a random factor in each trial  
  
head direction can be -1 (outward pointing), 0 (no head) or 1  
(inward pointing); 0 is not used in the present design  
  
  
Written by N. Ruh, 15/02/2008.  
  
### Exemplary reference:  
  
  Restle F & Decker J (1977) Size of the Mueller-Lyer illusion as a  
  function of its dimensions: Theory and data. Perception & Psychophysics 21:489 503  
  
History:  
3/3/2008  Included in Psychtoolbox (MK).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/PsychExampleExperiments/MullerLyerIllusion.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/PsychExampleExperiments/MullerLyerIllusion.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/PsychExampleExperiments/MullerLyerIllusion.m</code>
</div>

