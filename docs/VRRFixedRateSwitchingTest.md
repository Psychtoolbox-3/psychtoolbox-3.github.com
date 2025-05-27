# [VRRFixedRateSwitchingTest](VRRFixedRateSwitchingTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[VRRFixedRateSwitchingTest](VRRFixedRateSwitchingTest)([test='upstep'][, n=2000][, hwmeasurement=0][, testImage][, saveplots=0][, screenNumber=max])  
  
Test accuracy of Fixed refresh rate (FRR) stimulation, while rapid refresh rate  
switching is facilitated by use of VRR functionality, aka "[FreeSync](FreeSync)", "G-Sync",  
or "[DisplayPort](DisplayPort) Adaptive Sync".  
  
FRR switching is useful for paradigms where you want to have fine-grained control  
over video refresh rate, e.g., to play back movies or show animations at a specific  
framerate, and you want very stable timing, but you only occassionally need to  
switch framerates. FRR switching is fast, it only takes one or at most two video  
refresh cycles. However, during those 1-2 cycles, the display may blank or flicker.  
You may want to use FRR switching between consecutive trials to avoid flicker.  
  
Normal VRR modes allow equally fine-grained timing control and perfectly seamless  
changes of frame duration on a frame-to-frame basis. However, the current  
implementation may be a bit more noisy in terms of timing stability.  
  
The test exercises fast FRR switching on a suitable system. Currently only AMD  
graphics cards under Linux X11 with [DisplayPort](DisplayPort) connected VRR display monitors  
are supported, no other graphics cards, no HDMI connected displays, no other  
displays. You may need to run [PsychLinuxConfiguration](PsychLinuxConfiguration)(), make sure that the  
deep color config file gets installed or updated by it, and reboot your machine  
once to make this work on many Linux kernels.  
  
It submits [OpenGL](OpenGL) bufferswaps / flips of varying 'delay' between successive  
flips and measures and plots how well the hw can follow the requested timing.  
When appropriate, the fixed refresh rate of the display is switched via rapid  
switching, to achieve a frame interval as close as possible - or identical - to  
the requested delay. This works especially well within the VRR range of your  
display, typically between 48 Hz and the maximum refresh rate of your display.  
  
### Usage:  
  
All parameters are optional.  
  
### The 'test' parameter selects the test pattern:  
  
'upstep'    Stepwise increasing duration every 60 flips.  
  
'downstep'  Stepwise decreasing duration every 60 flips.  
  
'const'     Run at some constant frame duration.  
  
  
'n' Number of flips / trials to run. 2000 by default.  
  
  
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
  
5 = Measure via a supported photo-diode via [PsychPhotodiode](PsychPhotodiode)().  
  
6 = Produce light-flash pattern to drive external photo-diode. Don't record yourself.  
  
  
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
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/VRRFixedRateSwitchingTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/VRRFixedRateSwitchingTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/VRRFixedRateSwitchingTest.m</code>
</div>

