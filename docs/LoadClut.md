# [LoadClut](LoadClut)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[err]=[LoadClut](LoadClut)(windowPtrOrScreenNumber,clut,[startEntry],[bits])  
  
Load the hardware color lookup table (CLUT) of a video screen. It uses  
[Screen](Screen)('LoadCLUT'), as appropriate, to leave the hardware CLUT  
containing the numbers you provide in "clut", with no transformation.  
There \*are\* restrictions: On Microsoft Windows you can't use [CLUTs](CLUTs) for  
animation, as the operating system requires all [CLUTs](CLUTs) to contain mono-  
tonically increasing entries. Psychtoolbox currently has no way of  
detecting the resolution of your graphics cards DAC, so unless you  
explicitly provide the DAC resolution in the optional parameter 'bits',  
it will always assume a 8-Bit DAC. This assumption is safe, but it does  
not allow you to automatically take advantage of higher resolution [DACs](DACs).  
Apart from that, all pixelSizes are supported. It should works with all  
graphics cards on [MacOS](MacOS)-X, Windows and Linux. Fully supports 8-or-more-bit  
[DACs](DACs).   
  
We \*strongly\* suggest that all users use [Screen](Screen)('LoadNormalizedGammaTable')  
in new code. Its values range between 0.0 and 1.0 and are independent  
of DAC size, the system automatically maps the range 0.0 - 1.0 to the  
range really available on your graphics card, so no need for you (or for   
Psychtoolbox) to know the resolution of your graphics cards DAC. You will  
always automatically benefit from the highest possible resolution of your  
graphics card.  
  
  
### FUNCTION ARGUMENTS:  
  
The err return argument is only here for backwards compatibility to  
the old Psychtoolbox. It always will be empty.  
  
"clut", the user-supplied color table, should be a clutSizex3 matrix.  
Each row in the "clut" matrix is loaded into an RGB entry in the  
hardware CLUT. The values of the matrix elements should be integers in  
the range 0 to 2^bits-1.  
  
The maximum clut size is 256 rows, but you can pass less rows if you only  
want to change a portion of the hardware CLUT.  
  
"startEntry" is optional and determines which hardware CLUT entry to  
load first. Entries are numbered from 0 up. The default is 0. The first  
element of "clut", i.e. clut(1), will be loaded into hardware entry  
"startEntry".  
  
"bits" specifies how many bits you want to write to the CLUT. Typically  
it will be 8 bits, which is the default value. If you set it to  
some other value, the range of allowable entries scales accordingly.  
Thus if you use a 10-bit CLUT, then each entry should be between 0 and  
1023, etc.  
  
### GRAPHICS CARDS WITH MORE-THAN-8-BIT DACS:  
  
Some ATI Radeon's have 10-bit [DACs](DACs). The BITS++ adapter from Cambridge  
Research Systems has 14-bit [DACs](DACs).  
http://www.crsltd.com/catalog/bits++/  
  
See also [Screen](Screen) subfunctions 'LoadCLUT', 'LoadNormalizedGammaTable',  
'ReadNormalizedGammaTable'  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/LoadClut.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/LoadClut.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/LoadClut.m</code>
</div>

