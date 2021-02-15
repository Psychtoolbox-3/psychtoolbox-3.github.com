# [Screen('Resolution')](Screen-Resolution) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

oldResolution=Screen('Resolution', screenNumber [, newwidth][, newheight][, newHz][, newPixelSize][, specialMode]);

Query or change display settings for screen "screenNumber".  
Returns a struct "oldResolutions" with the current settings for screen  
resolution, refresh rate and pixel depth. Optionally sets new settings for  
screen resolution "newwidth" x "newheight", refresh rate "newHz" and framebuffer  
pixel depth "newPixelSize". Providing invalid or incompatible settings will  
raise an error. Especially the color depth "newPixelSize" should usually not be  
set to anything else than its default of 32 bpp or 24 bpp, iow. it should be  
best left alone. Other settings can impair alpha-blending on some systems, a  
setting of 16 bpp will disable alpha-blending and create drastically reduced  
color resolution of  5 bits per color channel. A setting of 8 bpp is not  
supported at all on [MacOS](MacOS)/X and will create artifacts on all other systems. Use  
a size of 32 bpp even for clut animation. This function may not work on all  
MS-Windows setups, your mileage may vary...  
On Linux/X11 with the classic X-Server, the function only switches display  
settings in the conventional sense on a single-display setup, or on a  
multi-X-screen setup with one display per X-[Screen](Screen). On a  
multi-display-per-X-[Screen](Screen) setup, this function only changes the total size of  
the framebuffer, ie., 'newwidth' and 'newheight', the other parameters are  
silently ignored. You can create X-Screens and fullscreen onscreen windows that  
are bigger than what is actually displayable on your attached displays. This  
allows for some interesting special tricks if you know what you are doing, but  
can also cause quite a bit of confusion. We recommend using this function on  
setups with a single display or a single display for each X-[Screen](Screen) (as listed by  
[Screen](Screen)('Screens'). On Linux/X11 setups with multiple attached displays per  
X-[Screen](Screen), the video settings of each individual display, e.g., resolution, video  
refresh rate, panning, can be queried and changed via the  
[Screen](Screen)('ConfigureDisplay') function instead. This allows for more flexibility,  
e.g., you can have a framebuffer bigger than the combined resolution of all  
displays and only show a fraction of it. You can change the relative position of  
all physical displays, configure "mirror modes", "side by side", or "on top of  
each other" display configurations.  
Psychtoolbox will automatically restore the systems display resolution to the  
system settings made via the display control panel as soon as either your script  
finishes by closing all its windows, or by some error. Terminating Matlab due to  
quit command will also restore the system preference settings. On a  
multi-display Linux setup, display settings are never automatically restored.  
If you call this command without ever opening onscreen windows and closing them  
at some point, Psychtoolbox will not restore display settings automatically.  
You can query a list of all supported combinations of display settings via the  
[Screen](Screen)('Resolutions') command. "specialMode" is a flag you must not touch,  
unless you really know what you're doing, that's why we don't tell you its  
purpose.  


###See also:
Screen('Resolutions')
