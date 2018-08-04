# [PsychProPixx](PsychProPixx)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[DatapixxToolbox](DatapixxToolbox)>[DatapixxBasic](DatapixxBasic)

[PsychProPixx](PsychProPixx)() - Drive fast display modes of [ProPixx](ProPixx) projectors.  
  
This function is an EXPERIMENTAL PROTOTYPE. It is subject  
to backwards incompatible change, or maybe even complete  
removal from future Psychtoolbox versions without warning!  
If you intend to use it in your own experiments, better make  
a private copy of the function file, or be prepared to rewrite  
your experiment code after Psychtoolbox updates.  
  
This function provides a preliminary method to setup Psychtoolbox  
for the fast display modes of the [ProPixx](ProPixx) projector and to use those  
modes in a convenient and relatively efficient fashion.  
  
See [PropixxImageUndistortionThrowaway](PropixxImageUndistortionThrowaway).m for a preliminary demo  
on how to use this function.  
  
  
### Subcommands and their meaning:  
  
[PsychProPixx](PsychProPixx)('SetupFastDisplayMode', window, rate [, flipmethod=0][, localcalibration=none][, dogpumeasure=0]);  
-- Setup for Propixx fast display mode. 'window' is the handle of  
the onscreen window which displays on the [ProPixx](ProPixx). 'rate' is the  
desired update rate, 4 for 4-fold rate (= 120 \* 4 = 480 Hz), or  
12 for 12-fold rate (= 120 \* 12 = 1440 Hz). 'flipmethod' method  
of flipping the stimulus images onto the screen. 0 = Standard  
[Screen](Screen)('[Flip](Flip)'), 1 = [Screen](Screen)('AsyncFlipBegin') async flips,  
2 = Optimized non-blocking flips with later retrieval of timestamps  
via [PsychProPixx](PsychProPixx)('GetTimingSamples'). Method 2 is the most efficient  
method, but it is only supported on Linux with the open-source graphics  
drivers. Method 1 is likely the second most efficient method and should  
work on all operating systems, but returned timestamps need some  
understanding of the rules for async flips. Method 0 is the most easy  
to use on any system, but also likely the least efficient one.  
'localcalibration' Specify a calibration file for display geometry correction  
via a local method. This is usually slower than use of a global calibration,  
so better use that and leave this parameter [] empty.  
'dogpumeasure' If set to 1 then the actual processing time per frame  
on the graphics card (gpu) will be measured with high precision if the  
gpu + graphics driver supports this. This is useful for benchmarking and  
tuning of code. Results are returned in the global variable 'gpudur' and  
optionally plotted via [PsychProPixx](PsychProPixx)('DisableFastDisplayMode', 1);  
  
  
image = [PsychProPixx](PsychProPixx)('GetImageBuffer');  
-- Get an offscreen window suitable for drawing a stimulus into it,  
and then passing it to [PsychProPixx](PsychProPixx)('QueueImage', image);  
  
  
presenting = [PsychProPixx](PsychProPixx)('QueueImage', image [, tWhen]);  
- Queue a 'image' for presentation. 'image' must be a texture  
or [OffScreenWindow](OffScreenWindow) of proper size, ie., half the width and height  
of the onscreen window. The most easy way to get a matching  
offscreen window for drawing into and presentation is to use  
image = [PsychProPixx](PsychProPixx)('GetImageBuffer').  
  
Once a sufficient number of images are queued, the final  
image for driving the [ProPixx](ProPixx) projector is created and presented,  
either at the next video refresh, or at the optional target time  
'tWhen' - which is passed to the [Screen](Screen)('[Flip](Flip)') command. When  
this happens, the 'presenting' flag will return as either 1 in offline  
timestamping mode (flipmethod 2), or as the [Flip](Flip) timestamp of  
image onset for the whole composite image, otherwise it will return  
as 0 if an image has just been queued for presentation.  
  
If you pass a 'tWhen' value of -1 then the [Screen](Screen)('[Flip](Flip)') is not executed  
automatically. Instead 'presenting' is returned as 1 when a flip needs to  
be performed as soon as possible, and you need to manually call the function  
presenting = [PsychProPixx](PsychProPixx)('[Flip](Flip)' [, tWhen]); to trigger the actual flip. The  
return value 'presenting' has the same meaning as the one of 'QueueImage'.  
This allows to split queuing and processing of stimulus images from actually  
flipping. This allows to overlap cpu computations in Octave/Matlab with gpu  
rendering better, by putting the cpu computations mostly between 'QueueImage'  
and final '[Flip](Flip)'. This is mostly advantageous for flipmethod 0, and to some  
degree flipmethod 1, but not as efficient as using the Linux-only flipmethod 2.  
  
  
samples = [PsychProPixx](PsychProPixx)('GetTimingSamples');  
-- Returns '[Flip](Flip)' timestamps in the vector 'samples'. Depending  
on flipmode, either all samples of all presentations are returned  
(for flipmode 2 on Linux), or up to the most recent 1200 samples  
are returned (for flipmode 0 or 1 on all operating systems).  
  
  
[PsychProPixx](PsychProPixx)('DisableFastDisplayMode' [, plottimestamps]);  
-- Disable Propixx mode, reset internal variables etc. If the optional  
'plottimestamps' flag is set to 1 then plots are generated which show  
the collected durations of frame presentations, and potentially  
collected timestamps of gpu rendertime if benchmarking was enabled.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/PsychProPixx.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/PsychProPixx.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/PsychProPixx.m</code>
</div>

