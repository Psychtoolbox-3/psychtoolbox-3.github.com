# [VBLSyncTest](VBLSyncTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[VBLSyncTest](VBLSyncTest)(n, numifis, loadjitter, clearmode, stereo, flushpipe, synchronous, usedpixx, screenNumber)  
  
Tests syncing of Psychtoolbox to the vertical retrace (VBL) and demonstrates  
how to implement the old [Screen](Screen)('WaitBlanking') behaviour with  
[Screen](Screen)('[Flip](Flip)')...  
  
This script provides a means to test, how well PTB synchronizes  
stimulus onset and execution of Matlab/Octave with the vertical retrace  
(also known as vertical blank or VBL) on your specific hardware setup.  
  
The script first opens a double-buffered fullscreen window. Then it  
performs a monitor calibration timing loop to estimate the real monitor refresh  
interval (aka IFI): While the formula ifi = 1.0 / [Screen](Screen)('NominalFramerate') will  
return an ifi that is close to the real IFI, it will be a little bit off  
from the real value. The reason is unavoidable jitter in the manufacturing of  
graphics cards internal clock circuits, as well as some drift and jitter  
caused by instabilities and change in the power supply and operating  
temperature of your machine. To be on the safe side, we use a timing-loop  
to compute the real IFI as an average of the IFI's of a number of consecutive  
monitor refresh intervals.  
  
After the calibration you'll see a simple animation: A flashing rectangle  
moving from the top-left corner of the screen to the bottom-right corner.  
During this animation, which lasts 'n' frames, it collects information  
about the timing behaviour.  
  
At the end, a couple of graphs are shown to you that should allow you to  
assess the timing behaviour of your setup.  
  
The following parameters can be changed in order to simulate different  
loads and stimulus presentation timings to assess PTB's behaviour under  
different conditions.  
  
  
### PARAMETERS:  
  
n = Number of samples to take. E.g., n=1000 == Draw an animation  
consisting of 1000 frames.  
  
  
  
numifis = Number of monitor refresh intervals [(IFIs)]((IFIs)) between flips:  
0 == [Flip](Flip) at each vertical retrace: This is the old PTB 1.0.50 behaviour.  
Values of numifis\>0 will cause [Screen](Screen)('[Flip](Flip)') to wait for 'numifis'  
monitor refresh intervals before flipping the back- and front buffers in  
sync with the vertical retrace.  
  
This would be roughly equivalent to the following snippet of code in the old  
[MacOS9](MacOS9)-PTB:  
...  
[Screen](Screen)('WaitBlanking', windowPtr, numifis);  
[Screen](Screen)('CopyWindow', windowPtr, myOffscreenWindowwithStimulusPtr);  
...  
  
  
  
loadjitter = Simulated load with a random duration between 0 ms  
and loadjitter monitor refresh intervals: We wait for the specified  
amount of time to simulate the execution of other Matlab-code, e.g.,  
[KbChecks](KbChecks), [GetMouse](GetMouse), Matlab calculations ...  
  
  
  
clearmode = Change the behaviour of [Flip](Flip) after flipping.  
clearmode = 0 will clear your stimulus drawing surface to background color after flip.  
This is the behaviour as found in PTB 1.0.50. After [Flip](Flip) you start with an  
empty image and can draw a completely new stim.  
  
clearmode = 1 will not clear after a flip, but keep the contents of your stimulus  
image after the [Flip](Flip): This allows you to incrementally update/draw stimuli.  
  
clearmode = 2 will neither clear nor keep the drawing surface after [Flip](Flip), but leave the  
cleanup work to you. To be precise: The drawing surface will contain the  
stimulus image that was \*just shown\* on the screen. Think of [Flip](Flip) as if it would  
flip the front- and back-side of a sheet of paper: The current front side  
shows the stim to your subject, the current back side is where you draw.  
clearmode 2 will allow you to update the back side, which was the front  
side before the flip happened! This mode is useful if you want to save  
about 0.5-2 ms of time needed for mode 1 or 2 if you draw stimuli on very  
tight deadlines.   
  
  
stereo = Test timing of display of stereoscopic stimuli.  
stereo = 0 will show you a standard monoscopic display.  
stereo = 1 will use the OS-X stereo output facilities to show stereoscopic  
stimuli: OS-X will quickly alternate between two images at each monitor refresh,  
one for the left-eye, one for the right-eye, while generating proper  
control signals for LCD shutter glasses. This should work with [MacOS](MacOS)-X  
compatible stereo display hardware, e.g., [CrystalEyes](CrystalEyes) shutter glasses.  
  
  
flushpipe = Mark end of drawing commands to improve presentation timing.  
PTB knows a new command [Screen](Screen)('DrawingFinished') which, when properly used,  
will give PTB hints on how to optimize drawing of stimuli: This allows to draw  
more complex stimuli at higher monitor refesh intervals with reliable presentation  
timing. flushpipe enables/disables use of this new command.  
  
flushpipe = 0 Don't mark end of drawing commands.  
flushpipe = 1 Mark end of drawing commands to improve timing.  
  
  
synchronous = 0 Don't wait for drawing completion in [Screen](Screen)('DrawingFinished')  
synchronous = 1 Wait for completion - Useful for benchmarking and debugging,  
but degrades performance significantly in real experiments.  
  
  
usedpixx = 1 Use a [DataPixx](DataPixx)/[ViewPixx](ViewPixx)/[ProPixx](ProPixx) device for external  
timestamping of stimulus onset, as a correctness test for [Screen](Screen)('[Flip](Flip)')  
timestamping. Disabled (0) by default.  
usedpixx = 2 Additionally correct for the clock skew between the computer  
and [DataPixx](DataPixx) device.  
  
  
screenNumber =  Use a screen other than the default (max) for testing .  
  
  
### EXAMPLES:  
  
[VBLSyncTest](VBLSyncTest)(1000, 0, 0.6, 0, 0, 1, 0) -- Render 1000 consecutive frames,  
flip at each retrace , pausing for 0.6 frame durations after each flip.  
Clear the framebuffer after flip, don't use stereo output, but use the new  
"[DrawingFinished](DrawingFinished)" command.  
  
[VBLSyncTest](VBLSyncTest)(100, 10, 6, 1, 0, 1, 0) -- Render 100 frames,  
flip only every 10th monitor refresh interval ("[WaitBlanking](WaitBlanking)" for 10 refresh intervals),  
pause for 6 frame durations after each flip. Don't clear the framebuffer after  
flip, don't use stereo output, but use the new "[DrawingFinished](DrawingFinished)" command.  
  
[VBLSyncTest](VBLSyncTest)(100, 10, 6, 1, 1, 1, 0) -- Render 100 frames,  
flip only every 10th monitor refresh interval ("[WaitBlanking](WaitBlanking)" for 10 refresh intervals),  
pause for 6 frame durations after each flip. Don't clear the framebuffer after  
flip, use stereo output via "frame-sequential stereo", use the new "[DrawingFinished](DrawingFinished)" command.  
  
  
  
### THE PLOTS:  
  
### Explanation of how to read the plots:  
  
Figure 1 shows the time delta between start of the VBL of successive  
[Flip](Flip)'s: This value should be close to the requested delta as specified to  
[Flip](Flip), e.g., you set numifis=0 or numifis=1 on a 100 Hz monitor. Then  
delta should be close to 1000 ms / 100 Hz = 10 ms. If numifis=2, it  
should be close to two monitor refresh intervals = 20 ms...  
  
The green horizontal line denotes the proper delta value for your monitor  
refresh rate and 'numifis' value. The blue graph shows measured deltas. A  
jitter of less than +/- 1 ms indicates proper stimulus presentation timing -  
no skipped frames.  
  
  
Figure 2 shows the rasterbeam positions when flip took its internal  
timestamp: The values should be usually above the screen height, e.g., on  
a monitor resolution of 1200 x 1024 pixels, values should be above 1024.  
Values way below 1024 are also ok (e.g., < 100). This just means that  
your computer is either pretty slow, or connected to a flat-panel.  
Lots of randomly distributed values between 0 and 1024 would indicate sync trouble.  
  
  
Figure 3: Shows the estimated difference between requested presentation  
deadline and the real presentation deadline (start of VBL). Positive  
values indicate a deadline-miss and give you an indication of how much  
the deadline has been missed. Negative (or zero) values indicate that the  
deadline has been met. While the sign of this value is useful for assessing  
timing, the value itself is only meaningful for people who can read and  
fully understand the C source code and logic of 'Flips' implementation...  
  
Figure 4: Shows the difference (in milliseconds) between estimated  
start of VBL and return of the [Flip](Flip) command to Matlab. This is some  
indication of the processing overhead of [OpenGL](OpenGL), the Operating system and  
Psychtoolbox when executing '[Flip](Flip)'. It's also a lower bound for the  
timing delay when trying to synchronize start of acquisition devices to  
VBL.  
  
Figure 5: Shows the difference (in milliseconds) between estimated  
stimulus onset (aka end of vertical retrace, scanning beam starts  
at top of screen) and the end of [Flip](Flip). This is the crucial value, if you  
want to sync something like sound-playback, triggering of some  
data-acquisition device (fMRI, MEG, EEG, ...) to stimulus onset. It  
should give you a feeling of how well you can sync. It's possible that  
negative values are reported on fast machines - [Flip](Flip) returns ahead of  
time (while monitor is still in retrace state). This is fine because your  
Matlab-Code for triggering something will add additional delays... Values  
should be below 1-2 milliseconds on reasonably modern and correctly  
configured hardware.  
  
Figure 6: Is only displayed when flag 'synchronous=1' This figure shows  
the total accumulated time for all drawing commands from the last [Flip](Flip) to the  
[DrawingFinished](DrawingFinished) command. It allows you to get a feeling on how hard the  
graphics hardware has to work for drawing your stim - and if it is  
possible at all to draw the stim on your hardware, given your time  
constraints. During a normal experiment (without sync-flag), the  
execution times of your Matlab code (as measured, e.g., by tic and toc)  
and of the drawing commands don't add up, because the graphics hardware  
works in parallel to the Matlab code.  
  
  
Please read the code of this M-File carefully as an example of how to get  
the best possible presentation timing on PTB-OSX.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/VBLSyncTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/VBLSyncTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/VBLSyncTest.m</code>
</div>

