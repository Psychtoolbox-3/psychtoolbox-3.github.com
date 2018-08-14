# [Screen('ColorRange')](Screen-ColorRange) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Set or return the maximum color component value that PTB should allow for  
provided color values when drawing into a window 'windowPtr' or its associated  
Offscreen windows. 'maximumvalue' is the optional new setting for the maximum  
allowed color component value: PTB expects the values of provided color  
components (red, green, blue, alpha or intensity) to be in the range 0 to  
maximumvalue. 0 is mapped to minimum output intensity, maximumvalue is mapped to  
maximum output intensity, values outside the range 0-maximumvalue are  
automatically saturated (clamped) at zero or maximumvalue if clamping is  
enabled. Initially color range clamping is enabled and the maximumvalue defaults  
to the biggest integral number displayable by your video hardware, e.g., 255 for  
a standard 8 bit per color component framebuffer as present on most consumer  
graphics hardware.   
A maximumvalue == 1.0 has special meaning: A maximumvalue of 1.0 will enable PTB  
to pass color values in OpenGL's native floating point color range of 0.0 to  
1.0: This has two advantages: First, your color values are independent of  
display device depth, i.e. no need to rewrite your code when running it on  
higher resolution hardware. Second, PTB can skip any color range remapping  
operations - this can speed up drawing significantly in some cases.  
'clampcolors': By default, [OpenGL](OpenGL) clamps colors to the range 0-maximumvalue.  
Negative colors are clamped to zero, color values greater than maximumvalue are  
clamped to maximumvalue. If you set the optional flag 'clampcolors' to 0, PTB  
will disable color clamping on hardware that supports unclamped colors. This  
allows to pass arbitrary (even negative) floating point numbers as color values.  
This is useful in conjunction with special high dynamic range display devices  
and for certain image processing operations when using PTB's image processing  
pipeline. If your hardware/operating system does support shaders, but not  
unclamped colors, [Screen](Screen) will try to use a shader-based workaround to enable  
unclamped color processing despite missing hardware capabilities - This comes at  
some performance penalty. You can also force [Screen](Screen) to always use its own  
unclamped color implementation by setting 'clampcolors' to a value of -1. On  
some graphics hardware, this may increase the precision with which the color of  
drawn objects is handled, but again at some speed penalty.  
CAUTION: If you change the color range or clamping of an onscreen window with  
this function, the change will only affect textures and offscreen windows  
created \*after\* this function call, not ones created before. It's therefore  
recommended to execute this function immediately after creating an onscreen  
window to guarantee consistent behaviour of your code. Color values provided as  
uint8 arrays or as textures, e.g., from video capture, movies or  
[Screen](Screen)('MakeTexture') are not rescaled, asthey are (expected) to be in a proper  
format for the given color depth already. However, the [Screen](Screen)('MakeTexture')  
command has an optional flag 'floatprecision' that allows you to pass image  
matrices unclamped and with either 16 bpc or 32 bpc floating point color  
precision if you want.  
Additionally you can force [Screen](Screen)('MakeTexture') to apply the 'maximumvalue'  
setting to regular textures which are provided as Matlab double type matrices by  
setting the optional parameter 'applyToDoubleInputMakeTexture' to 1. This will  
allow an input range of double values between zero and 'maximumvalue' to make  
your code more consistent, but it will still limit the range of valid values to  
that range and will represent that range only with 8 bit for 256 different  
levels, ie., the description of the 'clampcolors' setting do not apply to such  
uint8 low-precision textures! For full precision unconstrained textures, you'll  
still need to set the 'floatprecision' flag accordingly, as such textures  
require more memory and processing resources.  


###See also:
[OpenWindow](Screen-OpenWindow) [OpenOffscreenWindow](Screen-OpenOffscreenWindow)
