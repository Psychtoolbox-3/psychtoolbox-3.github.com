# [Screen('FrameRate')](Screen-FrameRate) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

hz=Screen('NominalFrameRate', windowPtrOrScreenNumber [, mode=0][, reqFrameRate]);

Returns or sets the nominal video frame rate in Hz, as reported by your  
computer's video driver.  
'FrameRate' is an alias for 'NominalFrameRate'. By default, this function  
returns the nominal framerate, as reported by your operating system, rounded to  
the closest integral value. If you set the optional 'mode' flag to 1, then the  
framerate is returned without rounding to the closest integer, but at floating  
point precision, on systems that support this (macOS and Linux).  
GNU/Linux/X11 only: If you set the 'mode' flag to 2 and specify 'reqFrameRate',  
then [Screen](Screen) will try to quickly switch to a framerate as close as possible to  
'reqFrameRate' Hz. Invalid settings are rejected, returning a value of -1. On  
failure, 0 is returned to signal inability to switch refresh. On systems other  
than Linux, 0 is always returned to signal failure. On successfull framerate  
change the new resulting nominal framerate is returned with double precision.  
NOTE: This function allows fast and almost seamless video refresh rate switching  
on AMD graphics cards when used to drive a [FreeSync](FreeSync) capable display device. The  
'reqFrameRate' should be within the supported [FreeSync](FreeSync) refresh rate range of  
your display device, or this function may silently fail! On other graphics cards  
or on standard fixed refresh rate displays, this may or may not work, but it  
will likely result in a time consuming video modesetting operation, during which  
the display may go blank for up to multiple seconds.  
One limitation at the moment is that in a multi-display setup, your visual  
stimulation window must be fully or at least predominantly covering the display  
area of the primary video output monitor, as the refresh rate of that monitor  
will be assigned for [Screen](Screen)('[Flip](Flip)', ...) scheduling of stimulus onset time.  
Otherwise only immediate flips at each video refresh cycle will work with  
reliable timing. See 'help VRRSupport' for possibly more background and setup  
info.  
Due to manufacturing tolerances and other noise in your system, the real monitor  
refresh interval can differ slightly from the nominal values returned by this  
function. To query the real, measured framerate use [Screen](Screen)('GetFlipInterval')  
instead.   


###See also:
[FrameRate](Screen-FrameRate) [GetFlipInterval](Screen-GetFlipInterval)
