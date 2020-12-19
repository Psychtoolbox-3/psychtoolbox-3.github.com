# [PerceptualVBLSyncTest](PerceptualVBLSyncTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[PerceptualVBLSyncTest](PerceptualVBLSyncTest)([screen=max][, stereomode=0][, fullscreen=1][, doublebuffer=1][, maxduration=10][, vblSync=1][, testdualheadsync=0][, useVulkan=0])  
  
Perceptual synchronization test for synchronization of [Screen](Screen)('[Flip](Flip)') and  
[Screen](Screen)('WaitBlanking') to the vertical retrace.  
  
Arguments:  
'screen' Either a single screen handle, or none (in which case the  
display with the maximum id will be used), or a vector of two handles in  
stereomode 10, e.g., [0 1] if you want to output to screens 0 and 1. You  
can also pass a vector of two screens when stereomode is not set to 10.  
In this case two separate (non-stereo) onscreen windows will be opened on  
both displays and they will get flipped in multiflip mode 2. That means  
that the first display (first element of 'screen') is synced to VBL, but  
the 2nd one is synced to bufferswaps of the first one. This is a  
straightforward test to check if two displays of a stereosetup run with a  
synchronized retrace cycle (good!) or if they are phase-shifted or  
drifting against each other (not good!).  
  
'stereomode' Which stereomode to use? Defaults to zero, ie. no stereo.  
  
'fullscreen' Fullscreen presentation? Defaults to 1 ie. yes. In  
non-fullscreen mode, no proper synchronization of bufferswaps can be  
expected.  
  
'doublebuffer' Single- or double-buffering (1). Defaults to 1. In single  
buffer mode there is no sync to retrace, so this is a good way to  
simulate the tearing artifacts that would happen on sync failure, just to  
get an impression.  
  
'maxduration' Maximum runtime of test: Runs until keypress or maxduration  
seconds have elapsed (Default is 10 seconds).  
  
'vblSync' If 1, synchronize bufferswaps to vertical retrace of monitor,  
otherwise (setting 0) swap immediately without sync, ie., usually with tearing.  
  
'testdualheadsync' If non-zero, and 'vblSync' is zero, manually wait until the video  
scanout position reaches half the height of the display, then swap. If this  
is done on a multi-display setup and the video scanout cycles of all the  
participating displays are properly synchronized, you should see a "static"  
crack line roughly at half the height of the display, maybe a bit lower. If  
you see a wandering crack line, at least on some displays, or you see vertical  
offsets of the position of the crack line between displays, then the displays  
are not properly synchronized, ie., not suitable for artifact free binocular  
stimulation. Caveat: This logic has been developed and tested specifically  
for testing on Linux with a single X-[Screen](Screen) spanning multiple displays. It may  
or may not be suitable to assess other operating systems or display configurations.  
  
'useVulkan' If 1, try to use a Vulkan display backend instead of the  
[OpenGL](OpenGL) display backend. See 'help PsychVulkan'.  
  
After starting this test, you should see a flickering greyish background  
that flickers in a homogenous way - without cracks or weird moving patterns  
in the flickering area. If you see an imhogenous flicker, this means that  
synchronization of stimulus onset to the vertical retrace doesn't work due  
to some serious bug or limitation of your graphics hardware or its driver.  
If you don't know what this means, you can test this script with parameter  
doublebuffer == 0 to artificially create a synchronization failure.  
  
On many systems you should also see some emerging pattern of yellow horizontal lines.  
These lines should be tightly concentrated/clustered in the topmost area of  
the screen. Lots of yellow lines in the middle or bottom area or even  
randomly distributed lines indicate some bug in the driver of your graphics  
hardware. This is a common problem of all ATI graphics adapters on [MacOS](MacOS)-X  
versions earlier than OS-X 10.4.3 when running a dual-display setup...  
  
A second reason for distributed yellow lines could be bad timing on your  
machine, e.g., due to background activity by virus scanners or the Spotlight  
indexing service on OS-X. Turn these off for conducting your studies!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/PerceptualVBLSyncTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/PerceptualVBLSyncTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/PerceptualVBLSyncTest.m</code>
</div>

