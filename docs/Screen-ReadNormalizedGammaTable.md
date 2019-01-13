# [Screen('ReadNormalizedGammaTable')](Screen-ReadNormalizedGammaTable) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[gammatable, dacbits, reallutsize] = Screen('ReadNormalizedGammaTable', windowPtrOrScreenNumber [, physicalDisplay]);

Reads and returns the gamma table 'gammatable' of the specified screen or window  
'windowPtrOrScreenNumber'.  
Returns the output resolution of the video DAC as optional second argument  
'dacbits'. Will return dacbits=0 as a "Don't know" value if it is unable to  
query the real resolution of the DAC. Currently no operating system reports a  
trustworthy 'dacbits'.  
Will return the real number of slots in the hardware lookup table in optional  
return argument 'reallutsize'. Currently only OS-X and Linux report the real LUT  
size.  
On [MacOS](MacOS)-X, the optional 'physicalDisplay' flag can be set to 1, zero is the  
default. In this case, the 'windowPtrOrScreenNumber' argument (which then must  
be a real screen number, not a window index) selects among physically present  
display devices, instead of logical devices. This is important if you want to  
assign different gamma-tables to multiple displays in a 'clone' or 'mirror mode'  
configuration, as there is only one logical display, but multiple physical  
displays, mirroring each other. Please note that screen numbering is different  
for physical vs. logical displays. For a list of physical display indices, call  
[Screen](Screen)('Screens', 1);  
On GNU/Linux, the optional 'physicalDisplay' parameter selects the video output  
from which the gamma table should be read in multi-display mode. On Linux a  
screen can output to multiple video displays, therefore this parameter allows to  
query the individual gamma tables for each display. The default setting is -1,  
which means to read the gamma table of the primary output of the given screen.  
See help for [Screen](Screen)('LoadNormalizedGammaTable'); for infos about the format of  
the returned table and for further explanations regarding gamma tables.  


###See also:

