# [AsyncFlipTest](AsyncFlipTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[AsyncFlipTest](AsyncFlipTest) - Stress-Test & Benchmark async flips.  
  
This exercises the async flip implementation in some simulated  
workloads, to test its reliability on a given GPU + driver + operaring  
system combo, and to benchmark its timing behaviour.  
  
The reliability and performance of async flips depends strongly  
on the quality of the underlying graphics hardware (GPU), its  
device drivers and the operating system. When doing concurrent  
async flipping and drawing, the load is even higher, as is  
dependency on a specific system setup.  
  
This demo first runs a red flicker stimulus for basic testing,  
until you press any key. Then it runs more complex stimuli  
until you press any key or 10 seconds worth of stimulation have  
elapsed. Then various timing parameters are plotted.  
  
In the first part you should see homogeneous regular red  
flickering.  
  
In the second part you should see a monochrome (workload = 1),  
colorful (workload = 2) random dot image. For workload = 0  
you should see a black background, and in the center of the  
screen a rectangle with a flickering green background and a  
yellow text "Hallo ;-)". If you see something else, your  
operating system or graphics driver has a bug. If you see  
irregular flicker then your system is not up to the task at  
the current video refresh rate, ie., it skips many presentation  
deadlines due to some overload of the GPU or system.  
  
### Usage:  
  
[AsyncFlipTest2](AsyncFlipTest2)([screenid=max][, workload=0][, pollingwait=0]);  
  
screenid = Which screen to run on. Default = max screen.  
  
workload = Which drawing workload to simulate in test part II [0, 1 2].  
           See code for workloads. 0 Simulates drawing into offscreen  
           windows, then blitting those into onscreen window.  
           1 simulates large luminance texture workload.  
           2 simulate the kind of texture creation, upload and  
           drawing workload you would have when playing back 1920x1080p  
           HD video in color.  
  
pollingwait = Use 'AsyncFlipCheckEnd' instead of 'AsyncFlipEnd'  
              in 1st test?  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/AsyncFlipTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/AsyncFlipTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/AsyncFlipTest.m</code>
</div>

