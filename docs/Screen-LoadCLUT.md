# [Screen('LoadCLUT')](Screen-LoadCLUT) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

oldclut = Screen('LoadCLUT', ScreenNumber [, clut] [, startEntry=0] [, bits=8]);

Load or query the hardware gamma table of the specified screen. If you pass a  
new 'clut' hardware gamma table, then 'clut' needs to be a matrix with 1 to  
(256-startEntry) rows and 3 columns. Each row corresponds to a single color  
index value  and contains the Red- green- and blue values to use for output of a  
pixel of that color. If you provide 'startEntry' then the hardware clut is  
overwritten by your table starting at color index 'startEntry' instead of  
starting at index 0. You are free to provide a clut with only a few rows if you  
only want to update a subset of the color indices in the hardware clut. Column 1  
is the red value, column 2 is the green value and column 3 is the blue value  
that you want to load into the hardware clut for a specific index. Values in the  
table have to be in range between 0 (for dark pixel) and 'max' (for maximum DAC  
output intensity), where 'max' depends on the number of bits that the RAMDAC of  
your graphics hardware supports. Psychtoolbox currently has no way of knowing  
the bit-resolution of your RAMDAC, so you have to provide it in the optional  
argument 'bits'. If you don't provide a 'bits' setting, it defaults to a safe  
default of 8-Bits. Some examples for 'bits' vs. 'max': 8 bits (default) --\> max  
= 255. 9 bits --\> max=511. 10 bits --\> max=1023. 12 bits --\> max = 4095. On  
[MacOS](MacOS)-X and Linux, this function takes arbitrary clut-tables which makes it  
suitable for fast CLUT animation. On Microsoft Windows, only tables with  
monotonically increasing values are considered valid. Other tables get rejected  
by the operating system -- there's nothing we can do about this incredibly wise  
decision of the Microsoft system designers :( , so this function is not suitable  
for CLUT animation, but only for linearizing or calibrating display devices.  
PLEASE NOTE: [LoadCLUT](LoadCLUT) is only provided to keep old code from OS-9 PTB and old  
Windows PTB working. It is just a wrapper around 'LoadNormalizedGammaTable'. Use  
'LoadNormalizedGammaTable' for new code. That function is independent of DAC  
resolution as it takes values in a normalized range between 0.0 and 1.0 and  
always gives you the highest possible resolution for your gamma table, despite  
not knowing the real DAC resolution. This function returns the old CLUT as  
optional return argument. If you don't pass a clut, then it only returns the old  
CLUT.  


###See also:
[LoadNormalizedGammaTable](Screen-LoadNormalizedGammaTable) [ReadNormalizedGammaTable](Screen-ReadNormalizedGammaTable)
