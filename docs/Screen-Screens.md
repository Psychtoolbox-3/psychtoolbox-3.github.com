# [Screen('Screens')](Screen-Screens) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

screenNumbers=Screen('Screens' [, physicalDisplays]);

Return an array of screenNumbers. If this command is executed on Microsoft  
Windows in a multi-display configuration, then the following rule applies:  
[Screen](Screen) 0 is always the full Windows desktop. Screens 1 to n are corresponding to  
windows display monitors 1 to n. If you want to open an onscreen window only on  
one specific display, or you want to query or set the properties of a display  
(e.g., framerate, size, color depth or gamma tables), use the screen numbers 1  
to n. If you want to open a window suitable for stereo display on a dual display  
setup, use screen zero.  
When executed on OS/X with the optional 'physicalDisplays' flag set to 1, will  
enumerate the set of physical displays, which can be different from the set of  
logical displays that is returned by default. E.g., in mirror mode or clone  
mode, there is only one logical display, representing the mirror set of all  
physical displays. This is mostly useful to set, e.g., gamma tables on a per  
display basis, even if in mirror mode.  
  


###See also:

