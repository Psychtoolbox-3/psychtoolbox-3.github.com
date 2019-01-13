# [Screen('OpenOffscreenWindow')](Screen-OpenOffscreenWindow) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[windowPtr,rect]=Screen('OpenOffscreenWindow',windowPtrOrScreenNumber [,color] [,rect] [,pixelSize] [,specialFlags] [,multiSample]);

Open an offscreen window. This is simply an [OpenGL](OpenGL) texture that is treated as a  
window, so you can draw to it. Offscreen windows should be used to keep old code  
from OS-9 Psychtoolbox working, or if you need an offscreen drawing canvas for  
fast drawing, that you can later use as a texture. For quickly displaying  
premade Matlab image matrices, use the 'MakeTexture' command instead. It allow  
for significantly higher drawing speeds.  
You can specify a screen (any windowPtr or a screenNumber\>=0) or no  
screen(screenNumber=-1), but any real screen must already have an open [Screen](Screen)  
window when you call [OpenOffscreenWindow](OpenOffscreenWindow).  
"color" is the clut index (scalar or [r g b] triplet or [r g b a] quadruple)  
that you want to poke into each pixel as initial background color; default is  
white.  
"rect" specifies the size of the offscreen window If supplied, "rect" must  
contain at least one pixel. If a windowPtr is supplied, then "rect" defaults to  
the whole window. If a screenNumber is supplied then "rect" defaults to the  
whole screen. If a screenNumber of -1 is supplied, then "rect" defaults to the  
size of the main screen. (In all cases, subsequent references to this new  
offscreen window will use its coordinates: origin at its upper left.)  
"pixelSize" sets the depth (in bits) of each pixel. If you specify no screen  
(screenNumber=-1) then the default pixelSize is 32, but you can specify any  
legal depth: 8, 16, 24, 32. A pixelSize of 0 or [] is replaced by the default of  
32 bits per pixel. If you specify a screen number of windowPtr, then the default  
depth is that of the screen or window. If you run your script with the imaging  
pipeline enabled (imagingmode flag \> 0 in [Screen](Screen)('OpenWindow'), then all  
Offscreen windows always have 4 color channels RGBA and the selectable depths  
are additionally 64 bits or 128 bits, corresponding to 16 bits or 32 bits  
floating point precision per color component. If 64 bits are selected but the  
hardware does not support this in float precision, a 15 bit precision per color  
channel signed integer format will be tried instead. On [OpenGL](OpenGL)-ES hardware, only  
the 32 bpc float type or 8 bit integer type is supported, therefore a pixelSize  
of more than 32 will always get silently upgraded to 128 bits per pixel, if  
possible.  
'specialFlags' optional parameter to set special properties, defaults to zero.  
If you set it to 1 then the offscreen window is created in GL\_TEXTURE\_2D format  
if possible. Use of GL\_TEXTURE\_2D format is currently not automatically  
compatible with use of specialFlags setting 2.  
If you set 'specialFlags' to 2 then the offscreen window will be drawn with  
especially high precision, see specialFlags setting of 2 in help for  
[Screen](Screen)('DrawTexture') for more explanation.  
A 'specialFlags' == 8 will prevent automatic mipmap-generation for GL\_TEXTURE\_2D  
textures.  
A 'specialFlags' == 32 will prevent automatic closing of the offscreen window by  
a call to [Screen](Screen)('[Close](Close)');  
'multiSample' optional number of samples to use for anti-aliased drawing: This  
defaults to zero if omitted, ie., no anti-aliasing is performed when drawing  
into this offscreen window. If you set a positive non-zero number of samples and  
your system supports anti-aliased drawing to offscreen windows and the imaging  
pipeline is active, then [Screen](Screen) will try to allocate the offscreen window with  
at least the requested number of samples per pixel for anti-aliasing, but  
gracefully fall back to lower numbers if the hardware isn't capable of handling  
the requested number. Please note that anti-aliased offscreen windows can't be  
directly used for transformations in [Screen](Screen)('TransformTexture') or for drawing  
via [Screen](Screen)('DrawTexture') -- this is a hardware limitation. To display or use  
the content of an anti-aliased offscreen window you must first create a normal  
offscreen window of the same size and color format (same 'rect' and 'pixelSize'  
parameter), then use [Screen](Screen)('CopyWindow', antialiasedWindowhandle,  
normalWindowhandle); to copy the content to the normal offscreen window. This  
will perform the actual conversion into anti-aliased and displayable content.  
If the imaging pipeline is disabled, the 'multiSample' parameter will be  
silently ignored.  
  
NOTE: [Screen](Screen)'s windows are known only to [Screen](Screen) and must be closed by it, e.g.,  
[Screen](Screen)('[Close](Close)', w). Matlab knows nothing about [Screen](Screen)'s windows, so the Matlab  
CLOSE command won't work on [Screen](Screen)'s windows.   


###See also:
[OpenWindow](Screen-OpenWindow)
