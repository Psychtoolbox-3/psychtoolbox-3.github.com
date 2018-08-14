# [testsampletime](testsampletime)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkTests](EyelinkTests)

Routine to test timing of functions that sample eye position  
John Palmer, last revised 6/6/01  
  
Most tests are of "getsample" function at the bottom of this program.  
It uses 'newfloatsampleavailable' and 'newestfloatsample'.  
  
To run this test program, do an initial calibration, then press 'O'.  
View several fixation targets turning on and off.    
Output appears in MATLAB command window.  
As an option, one can disable the calibration and just measure timing.  
  
Part 1:  Measure time between sample events with three time bases:  
  eyelink time stamp in sample (always 4 ms interval)  
  getsecs time at time received (variable 1-6? ms)  
  eyelink time stamp of message sent on receiving sample (also var 1-6? ms)  
  (This last time base requires using EDFVIEW to read sample times by hand.)  
Conclusion:  sampling at roughly 4 ms period but quite variable by getSecs.  
Hint to think about: variability is often identical from trial to trial.  
  
Part 2:  Measure elapsed time of key functions  
   Of particular interest is the time from start recording to when the first  
sample is retrieved.  This value puts an upper bound on the delay between  
recording the eye movement and getting realtime feedback.  In my tests, this  
upper bound is 15-17 ms.  Eyelink suggests the actual delay is about 10 ms.  
  
Part 3:  One can also inspect the EDF file and examine the time stamps.  
   Of particular interest is the time from starting to the first recording.  
I observe a 15 ms delay from startblock to synctime.  
I also observed that the position of the first sample is within 2 ms or less   
the position of the eye at SYNCTIME.  
In addition, the first sample arrives less than 1 ms after SYNCTIME message.  
This suggests the lag between DOS record and sample at Mac and in   
transmitting the messages is not more than 1-2 ms.  
There still remains to measure the lag between eye and the DOS record  
  
5/29/01 Begun based on shorteyelinkdemo and testcalib  
5/30/01 Added measurements of sample time interval  
5/31/01 many improvements  
6/1/01  updated documentation  
6/4/01  using alt version of initwindow in meyelinkinit2  
6/5/01  fwc changed to work with new toolbox version 1.1  
6/6/01  v3, jp:  removed global "el", moved initeyelinkdefine after initialize  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkTests/testsampletime.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkTests/testsampletime.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkTests/testsampletime.m</code>
</div>

