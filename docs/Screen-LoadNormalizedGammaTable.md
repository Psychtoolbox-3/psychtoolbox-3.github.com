# [Screen('LoadNormalizedGammaTable')](Screen-LoadNormalizedGammaTable) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[oldtable, success] = Screen('LoadNormalizedGammaTable', windowPtrOrScreenNumber, table [, loadOnNextFlip][, physicalDisplay][, ignoreErrors]);

Load the gamma table of the specified screen or window  
'windowPtrOrScreenNumber'.  
You need to pass the new hardware gamma table 'table' as a 'nrows' rows by 3  
columns matrix. Each row corresponds to a single color index value in the  
framebuffer and contains the Red- green- and blue values to use for output.  
Column 1 is the red value, column 2 is the green value and column 3 is the blue  
value. Values have to be in range between 0.0 (for dark pixel) and 1.0 (for  
maximum intensity). Example: table(127,1)=0.67 would mean that the red color  
value 127 should be displayed with 67% of the maximum red-gun intensity,  
table(32, 3)=0.11 means that blue color value 32 should be displayed with 11% of  
the maximum blue-gun intensity. The range of values 0-1 gets mapped to the  
hardware with the accuracy attainable by the hardwares DAC's, typically between  
8 and 10 bits.  
The required number of rows 'nrows' is typically 256 for consumer graphics  
cards.  
If the 'loadOnNextFlip' flag is set to a value < 2 for updating the graphics  
cards gamma table then the following limits apply: On MS-Windows, only gamma  
tables with 256 rows are accepted for the graphis card. On OS-X you can also  
pass 512, 1024, 2048, ..., 65535 rows instead of 256 rows, although this only  
makes sense for few selected applications. On Linux/X11 with some pro-graphics  
cards, e.g., some [NVidia](NVidia) [QuadroFX](QuadroFX) cards, you can pass more than 256 rows,  
similar to OS/X.  
If you provide the index of an onscreen window as 'ScreenNumber' and you set the  
(optional) flag 'loadOnNextFlip' to 1, then update of the gamma table will not  
happen immediately, but only at execution of the [Screen](Screen)('[Flip](Flip)',  
windowPtrOrScreenNumber) command. This allows to synchronize change of both the  
visual stimulus and change of the gamma table with each other and to the  
vertical retrace. If the flag is set to its default value of zero then update of  
the gamma table will happen at the next vertical retrace (or immediately if the  
graphics driver doesn't support sync to vertical retrace). A 'loadOnNextFlip'  
flag of 2 will load the provided table not into the hardware tables of your  
graphics card, but into the hardware tables of special display devices, like  
e.g., the Bits++ box. It can also be used to load clut's for color lookup table  
animation. Read the section about 'EnableCLUTMapping' in the 'help PsychImaging'  
for info on how to enable and use color lookup table animation.  
On [MacOS](MacOS)-X, the optional 'physicalDisplay' flag can be set to 1, zero is the  
default. In this case, the 'windowPtrOrScreenNumber' argument (which then must  
be a real screen number, not a window index) selects among physically present  
display devices, instead of logical devices. This is important if you want to  
assign different gamma-tables to multiple displays in a 'clone' or 'mirror mode'  
configuration, as there is only one logical display, but multiple physical  
displays, mirroring each other. Please note that screen numbering is different  
for physical vs. logical displays. For a list of physical display indices, call  
[Screen](Screen)('Screens', 1);  
On GNU/Linux X11, the optional 'physicalDisplay' parameter selects the video  
output to which the gamma table should be applied in multi-display mode. On  
Linux/X11 a screen can output to multiple video displays, therefore this  
parameter allows to setup individual gamma tables for each display. The default  
setting is -1, which means to apply the (same) gamma table to all outputs of the  
given screen.  
The optional 'ignoreErrors' parameter, if set to 1, will ask the function to  
continue in the case that the operating system rejected a gamma table update,  
instead of aborting your script, if you requested an immediate update via  
'loadOnNextFlip' == 0. The optional 2nd return argument 'success' will be 1 on  
success, 0 on a rejected immediate update. 'ignoreErrors' will be ignored in  
case of deferred updates via 'loadOnNextFlip' \> 0.  
On OSX and Linux/X11, this function takes arbitrary gamma-tables which makes it  
suitable for CLUT animation, although you should rather avoid CLUT animation, or  
use the [PsychImaging](PsychImaging)(...'EnableCLUTMapping'...) method instead. CLUT animation  
nowadays is almost always the wrong approach. If you really need it, the  
[PsychImaging](PsychImaging)() based method provides cross-platform compatibility and reliable  
timing for CLUT animation.  
On Microsoft Windows, only tables with monotonically increasing values are  
considered valid. Other tables get rejected by the operating system, so this is  
not suitable for CLUT animation, but only for linearizing or calibrating display  
devices. Microsoft Windows does impose additional unknown constraints beyond  
monotonicity, so generally anything not resembling a regular gamma calibration  
table may prove troublesome. Similar limitations currently apply to Linux when  
used with the Wayland display server.  
The function returns the old gamma table as optional 1st return argument and a  
success status code of 1 on success, 0 on failure as 2nd optional return  
argument in case of an immediate update (ie 'loadOnNextFlip' == 0).  
  


###See also:
[ReadNormalizedGammaTable](Screen-ReadNormalizedGammaTable)
