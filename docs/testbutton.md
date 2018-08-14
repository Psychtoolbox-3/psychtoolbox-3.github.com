# [testbutton](testbutton)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkTests](EyelinkTests)

John Palmer  
test button input of eyelink.  Simple version w/o file i/o  
Times using both eyelink timestamp and local computer clock  
runs till holding down key on keyboard while pressing button  
prints out by keypress:  button, states, eyelink time, getsecs time, overhead, diffs  
7/1/02  bug w/ eyelink time doesn't work, not even intializing variable????  
7/12/02 new MEX version w/ modified lastbuttonpress, works fine  
7/15/02 v6:  used lastbuttonpress to get initial time baseline  
7/16/02 v7:  used currenttime to get initial time  
7/18/02 v8:  used the new requesttime and readtime routines  
7/19/02 v9:  broke out routine [EXGetEyeLinkTime](EXGetEyeLinkTime), v10:  put in separate file  
7/25/02 fwc renamed to testbutton  
  
Typical Results:  
getsecs overhead 0.02 ms  
[EXGetEyeLink](EXGetEyeLink) overhead 0.60 ms  
random error in eyelink time ~ +-0.50 ms, good for a ms clock!  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkTests/testbutton.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkTests/testbutton.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkTests/testbutton.m</code>
</div>

