# [VRRTest](VRRTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[VRRTest](VRRTest)([test='sine'][, n=2000][, maxFlipDelta=0.2][, hwmeasurement=0][, testImage][, saveplots=0][, screenNumber=max])  
  
Test accuracy of VRR stimulation with variable timing, aka "[FreeSync](FreeSync)",  
"[DisplayPort](DisplayPort) Adaptive Sync", "HDMI VRR" or "G-Sync".  
  
The test exercises VRR on a suitable system, see "help [VRRSupport](VRRSupport)" for setup  
instructions, general info and caveats.  
  
It submits [OpenGL](OpenGL) bufferswaps / flips of varying 'delay' between successive  
flips and measures and plots how well the hw can follow the requested timing.  
  
### Usage:  
  
All parameters are optional.  
  
### The 'test' parameter selects the test pattern:  
  
'sine'      Sine wave, smoothly changing. Exceeds VRR range to test low framerate  
            compensation (lfc). 'sine' is the default pattern if parameter is omitted.  
  
'random'    Randomized from flip to flip, within VRR range.  
  
'maxrandom' Randomized from flip to flip, extending outside VRR range.  
  
'upsweep'   Linear increasing duration.  
  
'downsweep' Linear decreasing duration.  
  
'upstep'    Stepwise increasing duration every 60 flips.  
  
'downstep'  Stepwise decreasing duration every 60 flips.  
  
'const'     Run at some constant frame duration.  
  
  
'n' Number of flips / trials to run. 2000 by default.  
  
  
'maxFlipDelta' Maximum frame duration in seconds. 0.2 secs = 200 msecs by default.  
  
  
### 'hwmeasurement' Use external measurement hardware to get timing ground-truth:  
  
0 = Off [Default]. This display a static 'testImage' to allow to check how much  
    the VRR display flickers under different stimulation timing regimes.  
  
1 = [VPixx](VPixx) [DataPixx](DataPixx) or similar [VPixx](VPixx) device.  
  
2 = [VideoSwitcher](VideoSwitcher) + [RTBox](RTBox) TTL pulse input port. Works with [RTBox](RTBox), but also with  
    emulated [RTBox](RTBox) of the CRS Bits\#. Takes TTL pulse input from the [VideoSwitcher](VideoSwitcher).  
    Selecting this will execute a enable/disable sequence for the [VideoSwitcher](VideoSwitcher)  
    at start and end of a measurement session.  
  
3 = CRS Bits\# via a loopback cable from trigger out to trigger in BNC port.  
    Careful: Uses T-Lock for signalling/triggering at stimulus onset and therefore  
    a rather deficient (mis)design. This works as long as low framerate compensation  
    does not get triggered, otherwise the reference timestamps from the CRS hardware  
    will be completely useless and bogus trash!  
  
4 = Like 2 -- [RtBox](RtBox) pulse input, but for use with a [ColorCal2](ColorCal2) or photo-diode that  
    sends a TTL pulse to the [RtBox](RtBox) / Bits\# BNC trigger input instead of [VideoSwitcher](VideoSwitcher).  
  
  
'testImage' Either the name of an image file, or a numeric m x n or m x n x 3  
matric with color values. The image read from the image file, or given image  
matrix, will be displayed covering the full window in hwmeasurement == 0 mode.  
If the parameter is omitted, one of Psychtoolbox default demo images will be  
displayed. The purpose of this static image display is to test how much the  
display device flickers under different VRR stimulation timings.  
  
  
'saveplots' Should plots with results be saved to filesystem? Defaults to  
0 for 'No', 1 = 'Yes'.  
  
  
'screenNumber' Number of screen to test on. Maximum X-[Screen](Screen) by default.  
  
  
You can abort the test earlier by pressing the ESC key.  
  
The main plot figure will plot actual measured delay between successive flips  
(blue) against requested optimal duration (red). It will also show the difference  
in green and median error in red at the bottom of the graph. Median/Average error  
and standard deviation is printed to the console last. The plot is also saved  
to the current working directory as PDF file.  
  
  
### Preliminary results with a patch-set targeted at Linux 5.2:  
  
Testing on a Linux 5.3 kernel showed good behaviour on tested AMD  
DCE-8 (Sea Islands), DCE-11 (Polaris) and DCN-1 (Raven) gpu's within the VRR  
range of the monitor. Also pretty good behaviour on DCN-1 for flip rates below  
the minimum VRR rate by use of low framerate compensation. lfc performance was  
mixed on the DCE-8 and DCE-11 gpu's. For 'upsweep', 'upstep' and some 'const'  
duration it was pretty reasonable or as good as DCN-1. For 'downsweep' and  
'downstep' and some 'const' durations, lfc didn't do a great job, with actual  
frame durations often deviating by dozens of msecs from requested ones.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/VRRTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/VRRTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/VRRTest.m</code>
</div>

