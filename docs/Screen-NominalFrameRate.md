# [Screen('NominalFrameRate')](Screen-NominalFrameRate) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Returns or sets the nominal video frame rate in Hz, as reported by your  
computer's video driver. 'FrameRate' is an alias for 'NominalFrameRate'. By  
default, this function returns the nominal framerate, as reported by your  
operating system, rounded to the closest integral value. If you set the optional  
'mode' flag to 1, then the framerate is returned without rounding to the closest  
integer, but at floating point precision, on systems that support this [(MacOS]((MacOS)-X  
and Linux). GNU/Linux only: If you set the 'mode' flag to 2 and specify  
'reqFrameRate', then Psychtoolbox will try to change the current video refresh  
rate of the display: If 'reqFrameRate' is above 10.0, [Screen](Screen) will try to switch  
to a framerate as close as possible to 'reqFrameRate' Hz. If 'reqFrameRate' is a  
positive or negative value smaller than 10.0, then the video setting will be  
changed by 'reqFrameRate' system dependent units. The new settings that would  
result are validated to make sure they are safe for your display. Invalid  
settings are rejected, returning a value of -1. On systems other than Linux, 0  
is always returned to signal failure. On successfull framerate change, the new  
resulting nominal framerate is returned with double precision. NOTE:  
'reqFrameRate' must be pretty close to the initial framerate, e.g. initial +/- 2  
Hz. It is not possible to apply big changes, e.g., from 60 Hz to 75 Hz. This  
function is meant for fine-tuning the video refresh interval for the purpose of  
synchronizing different displays or the display and other stimulation- or  
acquisition devices. You can compensate for small phase-shifts or deviations...  
Due to manufacturing tolerances and other noise in your system, the real monitor  
refresh interval can differ slightly from the nominal values returned by this  
function. To query the real, measured framerate use [Screen](Screen)('GetFlipInterval')  
instead.   


###See also:
[FrameRate](Screen-FrameRate) [GetFlipInterval](Screen-GetFlipInterval)
