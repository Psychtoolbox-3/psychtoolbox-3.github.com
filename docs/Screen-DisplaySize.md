# [Screen('DisplaySize')](Screen-DisplaySize) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[width, height]=Screen('DisplaySize', ScreenNumber);

Return the physical width and height of the output display device associated  
with 'ScreenNumber'. The size is returned in units of millimeters as reported by  
the display device itself to the OS. On [MacOS](MacOS)-X, if Extended Display  
Identification Data (EDID) for the display device is not available, the size is  
estimated by OS-X based on the device width and height in pixels, with an  
assumed resolution of 2.835 pixels/mm or 72 DPI, a reasonable guess for displays  
predating EDID support. On M$-Windows and GNU/Linux, the behaviour in case of  
missing EDID data is unknown. This function returns a width and height of zero  
if physical display size can't be queried from the operating system. Please  
handle the returned information with great caution. It is unclear how accurate  
the EDID data for typical monitors or video beamers really is. This information  
could be pretty unreliable and therefore misleading!  


###See also:

