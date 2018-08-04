# [GetSecsTest](GetSecsTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[GetSecsTest](GetSecsTest)([n=100000])  
  
This test is meant for Microsoft Windows only!  
  
Performs a reliability test of your systems timing hardware. This script  
tries to find out if your systems clock works correctly, ie., if  
[GetSecs](GetSecs)(), [WaitSecs](WaitSecs)(), [Screen](Screen)('[Flip](Flip)') and the [PsychPortAudio](PsychPortAudio) functions  
for timed stimulus onset and clock queries will work correctly.  
  
The optional parameter 'n' specifies how many samples to use for each  
test run. A larger number means longer runtime, but higher accuracy of  
the results. Default is 100000 samples.  
  
The test shows a lot of different data plots, but you should focus on the  
results printed to the Matlab command window. If they sound ok then you  
can probably ignore the plots.  
  
The test exercises your timing hardware: It takes 'n' time samples in a  
loop which repeatedly asks [GetSecs](GetSecs) for the time. [GetSecs](GetSecs) is used in a  
special debug-mode which also provides time readings from an alternative  
hardware clock. After sampling, the script compares timestamps from the  
normally used high precision timer against samples taken from the low  
precision reference timer. In an ideal world on a well working system,  
both timers should deliver roughly the same time readings. A fixed offset  
between the two clocks is normal - they both count time from system  
bootup or reset, but they are started with a slight offset at system  
start. A slowly drifting offset is not uncommon on lower quality  
hardware, this is considered ok as long as the drift is small. Important  
is that time is monotonically increasing on both clocks and that the  
ratio of elapsed time in both clocks is nearly the same: Dividing elapsed  
time as reported by the high-res timer by the elapsed time reported by  
the low-res timer should yield a ratio of very close to 1.0. The test  
also checks for regular low-res timer ticks, if pause()'ing Matlabs  
execution for multiple seconds affects the clocks in some worrying  
manner (e.g., time slowing down) or if quick switching between multiple  
cpu cores of a multi-core machine causes time inconsistencies, e.g., time  
going backwards.  
  
The test first runs a block of trials with [PTBs](PTBs) timing in "normal mode",  
where PTB applies a couple of fixes for broken hardware.  
  
Then it disables those fixes and retests, to assess how earlier PTB  
versions worked on your system - when no such special workarounds were  
available.  
  
Please note that this test is not 100% water-proof, it could  
theoretically have 'false negatives', as many problems with the clocks  
are associated with the behaviour of system power management, which  
itself is influenced by all kind of factors, e.g., what other  
applications are running in parallel to Matlab, if there is any network  
traffic, what kind of hardware is connected to the system...  
  
We will try to improve the test as we learn more about possible causes of  
trouble.  
  
Starting with PTB releases as of 'beta' from 26th November 2007, PTB also  
performs a couple of runtime checks to spot more timer problems. These  
checks are performed all the time while your scripts are executing, so if  
you see some "CRITICAL-WARNING" messages about timer problems at the  
Matlab prompt while your scripts are executing, better take them serious!  
  
For more (up to date) information about system configurations that might  
suffer from clock problems, background information and troubleshooting  
tips, visit the Psychtoolbox Wiki's FAQ section, specifically:  
  
http://psychtoolbox.org/wikka.php?wakka=[FaqGetSecsTestFails](FaqGetSecsTestFails)  
  
Btw. Currently there are no known problems with timers and clocks on PC  
hardware running recent Linux distributions or on any Apple Macintosh  
computers running [MacOS](MacOS)/X ;-)  -- That's why first versions of this test  
are only targeted at MS-Windows.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/GetSecsTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/GetSecsTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/GetSecsTest.m</code>
</div>

