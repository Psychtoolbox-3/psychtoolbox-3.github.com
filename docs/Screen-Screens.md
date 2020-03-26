# [Screen('Screens')](Screen-Screens) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

screenNumbers=Screen('Screens' [, physicalDisplays]);

Return an array of screenNumbers, corresponding to available logical or physical  
displays.  
Please note that the set of reported screens is only refreshed on first  
invocation of [Screen](Screen)() after application startup or after a 'clear all'. If you  
replug or en-/disable displays, you must execute 'clear all' to force a  
redetection of available displays. This is done for efficiency reasons to get  
better realtime behaviour.  
The meaning/mapping of screenNumbers to physical display devices on different  
operating systems differs:  
On Linux with X11 X-Server display system, screenNumber 0 - n correspond to  
X-Screens 0 - n. As a single X-[Screen](Screen) can have multiple physical displays  
assigned, there isn't a one to one mapping by default. E.g., by default, all  
displays are assigned to X-[Screen](Screen) 0, so a multi-display setup will only report  
one screenNumber, the number 0. You can define arbitrary mappings with our setup  
script [XOrgConfCreator](XOrgConfCreator), to optimally suit your needs.  
If this command is executed on Microsoft Windows in a multi-display  
configuration, then the following rule applies: [Screen](Screen) 0 is always the first two  
monitors assigned to the Windows desktop. Screens 1 to n are corresponding to  
windows display monitors 1 to n. If you want to open an onscreen window only on  
one specific display, or you want to query or set the properties of a display  
(e.g., framerate, size, color depth or gamma tables), use the screen numbers 1  
to n. If you want to open a window suitable for stereo display on a dual display  
setup consisting of the first two monitors, use screen zero.  
On OSX, numbers 0 - n correspond to logical displays 0 - n. When executed on OSX  
with the optional 'physicalDisplays' flag set to 1, it will enumerate the set of  
physical displays, which can be different from the set of logical displays that  
is returned by default. E.g., in mirror mode or clone mode, there is only one  
logical display, representing the mirror set of all mirrored physical displays.  
This is mostly useful to set, e.g., gamma tables on a per display basis, even if  
in mirror mode. Note that according to some user reports, reporting of the true  
set of physical displays may have been broken by Apple in current macOS  
versions: The set of reported logical and physical displays may be the same even  
in mirror mode configurations, due to macOS operating system defects.  
  


###See also:

