# [PsychVideoSwitcher](PsychVideoSwitcher)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[PsychVideoSwitcher](PsychVideoSwitcher)(command [,arg1, arg2, .....]);  
  
Psychtoolbox support for the Xiangrui Li et al. "[VideoSwitcher](VideoSwitcher)" video  
attenuator device for high precision luminance output with up to 16 bits  
luminance resolution.  
  
This routine incorporates code contributed by Xiangru Li for switching  
between monochrome and color display mode and for performing the  
reference Matlab routines for image formatting.  
  
Options: 'command' is a command string, specifying a subcommand. The  
following subcommands are supported with the following options:  
  
### Public functions:  
  
  
[PsychVideoSwitcher](PsychVideoSwitcher)('SwitchMode', screenIdx, enableLuminanceMode [, [VideoSwitcherIsABox](VideoSwitcherIsABox)])  
- Switch programmatically between high precision luminance mode and  
standard RGB true color display mode. 'screenIdx' is the screen index of the  
for the display screen to switch.  
  
'enableLuminanceMode' is meaningful only for card [VideoSwitcher](VideoSwitcher), which  
must be set to 0 to switch to RGB mode, and to 1 to switch to high  
precision luminance mode. For box version, the [SwitchMode](SwitchMode) subfunction  
ignores the third input, and only toggles between two display modes,  
equivalent to pushing the switch button on the box.  
  
'VideoSwitcherIsABox' is an optional argument: If set to 1, then perform  
switching procedure for an external (box) device. If set to zero, then  
perform procedure for an internal (PCI card) device. If argument is  
omitted, the proper default type is read from a configuration file stored  
in the path mypath = [PsychtoolboxConfigDir](PsychtoolboxConfigDir)('VideoSwitcher');  
  
If you create a file named 'VideoSwitcherIsABox' in that directory  
mypath, the switcher is assumed to be an external box. If you create a  
file named 'VideoSwitcherIsACard', the code assumes a PCI card based  
device. If no such files exist, the switcher is assumed to be a box.  
  
It is important for the code to know if the switcher is a box or a card,  
as the switching strategy is different.  
  
  
[PsychVideoSwitcher](PsychVideoSwitcher)('SetTrigger', win, triggerLine [, count=infinite]);  
- Set trigger line and options for [VideoSwitcher](VideoSwitcher) connected to the display  
of onscreen window 'win'.  
  
'triggerLine' defines the vertical (y) position of a trigger line to be  
drawn to the green channel of the final image, in order to trigger the  
trigger-circuit of the [VideoSwitcher](VideoSwitcher). If you set it to a negative value  
or to empty [], triggering will be disabled (This is the default).  
  
'count' Optional: Number of redraw cycles (invocations of  
[Screen](Screen)('[Flip](Flip)')), that the triggerline should be drawn. If left out, the  
line will be drawn on each redraw until disabled. If set to some value,  
it will be drawn for 'count' number of redraws, then disabled.  
  
The trigger mechanism only works if the [VideoSwitcher](VideoSwitcher) is set to high  
precision luminance display. It will emit a TTL pulse of 100 microseconds  
duration when the triggerline is drawn by your display. Only one TTL  
trigger pulse per video refresh is possible.  
  
  
[PsychVideoSwitcher](PsychVideoSwitcher)('SetBackgroundLuminanceHint', win, luminance);  
- Tell the driver the 'luminance' value of the background pixels of  
onscreen windows 'win'. The driver will use this hint to optimize  
conversion of background pixels. This allows for a quite significant  
speedup if your stimulus only covers a fraction of the display area and  
the remaining area is just a uniform luminance background. This is only  
functional if you use the driver that uses the calibration LUT, not the  
simple driver.  
  
  
[RGBImage](RGBImage) = [PsychVideoSwitcher](PsychVideoSwitcher)('MapLuminanceToRGB', lum, ratio [, trigger]);  
- Perform conversion of a luminance image into a [RGBImage](RGBImage). This is a pure  
Matlab based implementation for graphics hardware that is not capable of  
supporting the imaging pipeline.  
  
 Inputs:  
    lum: luminance [(MxN]((MxN) matrix with values from 0 to 1)  
    ratio: blue to red ratio of the video switcher  
    trigger: when non-zero, a trigger will be sent in current frame  
        trigger=1 or 'top', the first line of image  
        trigger=2 or 'auto',  the first line with non-zero image  
        trigger=3 or 'middle', the middle line of image  
    If you omit ratio, you should give it in this code  
 Output: RGB image [(MxNx3]((MxNx3) matrix with values from 0 to 255)  
  
  
[RGBImage](RGBImage) = [PsychVideoSwitcher](PsychVideoSwitcher)('MapLuminanceToRGBCalibrated', lum, ratio, lut [, trigger])  
- Perform conversion of a luminance image into a [RGBImage](RGBImage). This is a pure  
Matlab based implementation for graphics hardware that is not capable of  
supporting the imaging pipeline.  
  
 Inputs:  
    lum: luminance [(MxN]((MxN) matrix with values from 0 to 1)  
    ratio: blue to red ratio of the video switcher  
    lut: The 257 slots calibrated luminance table as described below.  
    trigger: when non-zero, a trigger will be sent in current frame  
        trigger=1 or 'top', the first line of image  
        trigger=2 or 'auto',  the first line with non-zero image  
        trigger=3 or 'middle', the middle line of image  
    If you omit ratio, you should give it in this code  
 Output: RGB image [(MxNx3]((MxNx3) matrix with values from 0 to 255)  
  
Note: this runs slow when lum matrix is large. 200x200 can take 1 second.  
  
This uses the calibrated luminance table saved in calibratedlum.mat.  
For detail, check the paper http://lobes.usc.edu/Journals/JNM03.pdf  
  
### The steps to get the table:  
  
 1. Switch the video switcher to grayscale mode;  
  
 2. Set up the equipement to accurately measure screen luminance;  
    you can use a photometer or data acquisition system;  
  
 3. Measure 257 luminance levels at RGB of [0 0 b] and [btrr 0 255],  
    where b is 0:255, and btrr the blue to red ratio of switcher;   
  
 4. Store 257 luminance in a variable callum and normalize them:  
    callum=callum/callum(257);  
  
 5. Save it to a configuration file. See the help for subfunction  
    'GetDefaultConfig' below for how and where to store the calibration  
    table.  
  
  
[btrr, lut] = [PsychVideoSwitcher](PsychVideoSwitcher)('GetDefaultConfig', win);  
- Get default 'btrr' parameter and 'lut' lookup table from configuration  
files and return them. This function can be used by you to get switcher  
parameters for use with the Matlab conversion functions above. It will be  
automatically used by the imaging pipeline (by [PsychImaging](PsychImaging)() command) if  
you select [VideoSwitcher](VideoSwitcher) as an output device but don't provide explicit  
settings for 'btrr' and/or 'lut'.  
  
Configuration files for the [VideoSwitcher](VideoSwitcher) should be stored in the folder  
whose path you get if you type mypath = [PsychtoolboxConfigDir](PsychtoolboxConfigDir)('VideoSwitcher');  
  
You can store a configuration file specific to a display screen  
'screenid' (with the numbering as in [Screen](Screen)('Screens')). The file should  
have the name [SettingsforScreen](SettingsforScreen)\_X.mat with X being the screen number,  
e.g., [SettingsforScreen](SettingsforScreen)\_0.mat . This allows you to store per-display  
device settings. Alternatively you can store settings in a "global"  
config file named [GlobalSettings](GlobalSettings).mat if they are not specific to the  
display. The stored mat file should contain up to two variables:  
  
The variable 'btrr' should store the measured/calibrated BTRR  
Blue-To-Red-Ratio for yor switcher and display setup. This variable is  
mandatory.  
  
The optional variable 'lut' would be a 257 elements double vector of  
luminance calibration data, as described in the help text immediately  
above the help for this subfunction (== help for  
'MapLuminanceToRGBCalibrated').  
  
You would create such a file by typing, e.g.:  
btrr = 128;  
lut = the lookup table vector created by calibration...  
save 'GlobalSettings.mat' btrr lut  
  
  
  
  
Internal helper functions for Psychtoolbox - Must not be called from  
normal user code!!  
  
luttexid = [PsychVideoSwitcher](PsychVideoSwitcher)('GetLUTTexture', win, lut, btrr, shader);  
- Convert blue-to-luminance calibration lookup table 'lut' into a lookup  
table texture for the imaging pipeline, set it up and return a texture  
handle 'luttexid' to it. 'btrr' is the required BTRR value. 'shader' is  
the GLSL shader handle of the output formatting shader used.  
  
  
[PsychVideoSwitcher](PsychVideoSwitcher)(win);  
- If 'win' is a numeric onscreen window handle, perform all operations to  
implement the green channel trigger functionality for onscreen window  
'win'. This routine uses MOGL glXXX() functions to implement drawing of  
proper trigger pixel values to the green channel for trigger creation.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/PsychVideoSwitcher.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/PsychVideoSwitcher.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/PsychVideoSwitcher.m</code>
</div>

