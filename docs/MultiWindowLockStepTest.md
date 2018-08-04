# [MultiWindowLockStepTest](MultiWindowLockStepTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[MultiWindowLockStepTest](MultiWindowLockStepTest)([nrwins=10][, separateScreens=0]);  
  
Test if and how many parallel asynchronous window flips  
Psychtoolbox can handle on multiple onscreen windows.  
  
This test exercises the asynchronous flip scheduling and  
timestamping, aka the [Screen](Screen)('AsyncFlipBegin'); and  
[Screen](Screen)('AsyncFlipCheckEnd'); functions for parallel scheduling  
of multiple independent bufferswaps on multiple open onscreen  
windows.  
  
'nrwins' selects how many onscreen windows to drive in parallel.  
If set to [], 2 windows will be used. The i'th window is flipped  
at a target rate of one flip every i'th video refresh interval.  
  
Timestamps are collected for all flips and in the end one plot  
per window shows how well the flips met their requested deadlines.  
  
If 'nrwins' is omitted, a simple test with only two windows is  
conducted. One window flips after 10 seconds, the other after 20  
seconds.  
  
If the optional parameter 'separateScreens' is set to a non-zero  
setting, then the different onscreen windows are not opened  
on the same display screen 0, but each one on a separate screen.  
Performance can differ significantly between one screen and  
multi-screen, as the operating system will use very different  
underlying algorithms and methods to handle flips on windows,  
depending on their placement on different displays or not. Each  
operating system will also behave differently.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/MultiWindowLockStepTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/MultiWindowLockStepTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/MultiWindowLockStepTest.m</code>
</div>

