# [Screen('ConfigureDisplay')](Screen-ConfigureDisplay) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

oldSettings = Screen('ConfigureDisplay', setting, screenNumber, outputId [, newwidth][, newheight][, newHz][, newX][, newY]);

Query or change 'setting' for display output 'outputId' of screen  
'screenNumber'.  
This function allows you to configure the different attached display outputs of  
a virtual screen.  
Optionally sets new settings for that output.  
Possible values for subfunction parameter 'setting':  
'Brightness': Return or set brightness of an attached display device. Many  
displays and systems don't support this function.  To find out if your system  
supports brightness queries and setting, call this subfunction without  
specifying a brightness.  The function will either return a \>= brightness value,  
or -1 if the system doesn't support brightness control.  If you try to set  
brightness on a system that doesn't support it, the function will abort with an  
error.  Brightness values are in the range 0.0 to 1.0 from darkest to brightest.  
Returns old brightness setting.  
'AutoBrightnessMode': Set the [AutoBrightness](AutoBrightness) mode on supported systems, macOS  
only at the moment. If you call the function without specifying a new mode, it  
will return -1 if setting [AutoBrightness](AutoBrightness) is unsupported on the system, otherwise  
it will return the value 2 to confirm setting [AutoBrightness](AutoBrightness) should be possible.  
If you try to set [AutoBrightness](AutoBrightness) on a system that doesn't support it, the  
function will abort with an error. Otherwise it will return 2 to confirm it  
tried to set [AutoBrightness](AutoBrightness) mode and then try to set the mode you specified: A  
mode of 1 tries to enable [AutoBrightness](AutoBrightness), a mode of 0 tries to disable  
[AutoBrightness](AutoBrightness) on the given output. Please note that there isn't any feedback if  
switching [AutoBrightness](AutoBrightness) worked, or what the current or previous enable state of  
[AutoBrightness](AutoBrightness) is or was, as queries are not supported by macOS. Neither will  
there be reliable visual feedback in the macOS display settings GUI! This  
feature is experimental and may not work at any time for any reason!  
'NumberOutputs': Return number of active separate display outputs for given  
screen 'screenNumber'.  
'Capture': Capture output 'outputId' of a screen 'screenNumber' for exclusive  
use by Psychtoolbox.  
'Release': Release output 'outputId' of a screen 'screenNumber' from exclusive  
use by Psychtoolbox.  
Please note that 'Capture' and 'Release' are automatically applied to a display  
output as appropriate whenever a fullscreen onscreen window is opened or closed  
on a display. You usually don't need to call these functions yourself, in fact,  
you even shouldn't call them yourself usually, as wrong use of the functions can  
cause graphics malfunctions or even a freeze of the display or GUI, forcing you  
to kill Matlab or Octave as a last resort to regain control over your displays.  
The main purpose of these functions is to temporarily block all graphics  
operations or display updates on displays that are not used for visual  
stimulation, ie., not covered by fullscreen onscreen windows. This prevents  
other running applications from interfering with your experiment script by  
preventing them to take up valuable resources on the graphics card. Display  
capture is not supported on all operating systems in all modes of operation. If  
the functions get called on an unsupported configuration, they silently return  
and simply do nothing.  
  
'Dithering' Control digital display dithering on supported [GPUs](GPUs). This is  
currently only supported on AMD graphics cards under Linux and OSX.  
'screenNumber' will apply the setting on all video outputs connected to screen  
'screenNumber'. The next setting is the 'ditherEnable' flag: A value of zero  
will disable dithering. A non-zero value will reenable dithering if it was  
previous disabled by Psychtoolbox. If dithering wasn't disabled, then instead  
the given value will be written into the dither control register to modify  
dithering settings. The meaning of specific values is GPU and vendor specific  
and only useful for experts.  
Example call: [Screen](Screen)('ConfigureDisplay', 'Dithering', screenNumber,  
ditherEnable);   
  
'Scanout': Retrieve or set scanout parameters for a given output 'outputId' of  
screen 'screenNumber'. Returns a struct 'oldSettings' with the current settings  
for that output. Only supported on Linux.  
It returns and accepts the following optional parameters:  
  
\* Display resolution "newwidth" x "newheight", and nominal refresh rate "newHz".  
\* Panning ('newX','newY') - The location of the top-left corner of the display  
in the framebuffer.  
Readonly properties:  
  
\* Display size "displayWidthMM" x "displayHeightMM" in millimeters, as reported  
by attached display.  
\* Video output name "name".  
\* Video output handle "outputHandle". On Linux/X11 this is the numeric XID of  
the associated [RandR](RandR) video output.  
  
Providing invalid or incompatible settings will raise an error.  
  


###See also:
Screen('Resolutions'), Screen('Resolution');
