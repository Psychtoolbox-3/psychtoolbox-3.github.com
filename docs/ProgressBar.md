# [ProgressBar](ProgressBar)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[ProgressBar](ProgressBar)    Ascii progress bar.  
   progBar = [ProgressBar](ProgressBar)(nMax,str) creates a progress bar and returns a  
   pointer to a function handle which can then be called to update it.  
  
   To update, call progBar(currentStep)  
  
   Example:  
      n = 500;  
      progBar = [ProgressBar](ProgressBar)(n,'computing...');  
      for tmp = 1:n  
        progBar(tmp);  
        pause(.01)  
      end  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/ProgressBar.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/ProgressBar.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/ProgressBar.m</code>
</div>

