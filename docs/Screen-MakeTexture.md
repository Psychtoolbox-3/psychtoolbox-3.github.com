# [Screen('MakeTexture')](Screen-MakeTexture) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

textureIndex=Screen('MakeTexture', WindowIndex, imageMatrix [, optimizeForDrawAngle=0] [, specialFlags=0] [, floatprecision=0] [, textureOrientation=0] [, textureShader=0]);

Convert the 2D or 3D matrix 'imageMatrix' into an [OpenGL](OpenGL) texture and return an  
index which may be passed to 'DrawTexture' to specify the texture.  
In the [OpenGL](OpenGL) Psychtoolbox textures replace offscreen windows for fast drawing  
of images during animation.  
The imageMatrix argument may consist of one monochrome plane (Luminance), LA  
planes, RGB planes, or RGBA planes where A is alpha, the transparency of a  
pixel. Alpha values typically range between zero (=fully transparent) and 255  
(=fully opaque).  
The [Screen](Screen)('ColorRange') command affects the range of expected input values in  
'imageMatrix' matrices of double precision type, as does the optional  
'floatprecision' flag discussed below.  
You need to enable Alpha-Blending via [Screen](Screen)('BlendFunction',...) for the  
transparency values to have an effect.  
The argument 'optimizeForDrawAngle' if provided, asks Psychtoolbox to optimize  
the texture for especially fast drawing at the specified rotation angle. The  
default is 0 == Optimize for upright drawing. If 'specialFlags' is set to 1 and  
the width and height of the imageMatrix are powers of two (e.g., 64 x 64, 256 x  
256, 512 x 512, ...), or your graphics card supports so called non-power-of-two  
textures, then the texture is created as an [OpenGL](OpenGL) texture of type  
GL\_TEXTURE\_2D. Otherwise Psychtoolbox will try to pick the most optimal format  
for fast drawing and low memory consumption. GL\_TEXTURE\_2D textures are  
especially useful for animation of drifting gratings, for simple use with the  
[OpenGL](OpenGL) 3D graphics functions and for blurring. Use of GL\_TEXTURE\_2D textures is  
currently not automatically compatible with use of specialFlags settings 2 or 4.  
If 'specialFlags' is set to 2 then PTB will try to use its own high quality  
texture filtering algorithm for drawing of bilinearly filtered textures instead  
of the hardwares built-in method. This only works on modern hardware with  
fragment shader support and is slower than using the hardwares built in  
filtering, but it may provide higher precision on some hardware. PTB  
automatically enables its own filter algorithm when used with floating point  
textures or when [Screen](Screen)('ColorRange') is used to enable unclamped color  
processing: PTB will check if your hardware is capable of unrestricted high  
precision color processing in that case. If your hardware can't guarantee high  
precision, PTB will enable its own shader-based workarounds to provide higher  
precision at the cost of lower speed.   
If 'specialFlags' is set to 4 then PTB tries to use an especially fast method of  
texture creation. This method can be at least an order of magnitude faster on  
some systems. However, it only works on modern [GPUs](GPUs), only for certain maximum  
image sizes, and with some restrictions, e.g., scrolling of textures or  
high-precision filtering may not work at all or as well. Your mileage may vary,  
so only use this flag if you need extra speed and after verifying your stimuli  
still look correct. The biggest speedup is expected for creation of standard 8  
bit integer textures from uint8 input matrices, e.g., images from imread(), but  
also for 8 bit integer Luminance+Alpha and RGB textures from double format input  
matrices.  
A 'specialFlags' == 8 will prevent automatic mipmap-generation for GL\_TEXTURE\_2D  
textures.  
A 'specialFlags' == 32 setting will prevent automatic closing of the texture if  
[Screen](Screen)('[Close](Close)'); is called. Only [Screen](Screen)('[Close](Close)', textureIndex); would close the  
texture.  
'floatprecision' defines the precision with which the texture should be stored  
and processed. Default value is zero, which asks to store textures with 8 bit  
per color component precision, a suitable format for standard images read via  
imread(). A non-zero value will store the textures color component values as  
floating point precision numbers, useful for complex blending operations and  
calculations on the textures and for processing and display of high dynamic  
range image textures, either on a LDR display via tone-mapping, or on a HDR  
display. If floatprecision is set to 1, the texture gets stored in half\_float  
format, i.e. 16 bit per color component - Suitable for most display purposes and  
fast on recent gfx-hardware. A value of 2 asks for full 32 bit single precision  
float per color component. Useful for complex computations and image processing,  
but can be extremely slow when texture filtering is used on any piece of  
graphics hardware manufactured before the year 2007. If a value of 1 is  
provided, asking for 16 bit floating point textures, but the graphics hardware  
does not support this, then PTB tries to allocate a 15 bit precision signed  
integer texture instead, assuming the graphics hardware supports that. Such a  
texture is more precise than the 16 bit floating point texture it replaces, but  
can not store values outside the range [-1.0; 1.0]. On [OpenGL](OpenGL)-ES hardware, a 32  
bit floating point texture is selected instead.  
'textureOrientation' This optional argument labels textures with a special  
orientation. Normally (value 0) a Matlab matrix is passed in standard Matlab  
column-major dataformat. This is efficient for drawing of textures but not for  
processing them via [Screen](Screen)('TransformTexture'). Therefore textures need to be  
transformed on demand if used that way. This flag allows to short-cut the  
process: A setting of 1 will ask for immediate conversion into the optimized  
format. A setting of 2 will tell PTB that the Matlab matrix has been already  
converted into optimal format, so no further processing is needed. A value of 3  
tells PTB that the texture is completely isotropic, with no real orientation,  
therefore no conversion is required. This latter setting only makes sense for  
random noise textures or other textures generated from a distribution with  
uncorrelated noise-like pixels, e.g., some power spectrum distribution.  
'textureShader' - optional: If you provide the handle of an [OpenGL](OpenGL) GLSL shader  
program, then this shader program will be executed (bound) during drawing of  
this texture via the [Screen](Screen)('DrawTexture',...); command -- The normal texture  
drawing operation is replaced by your customized algorithm. This is useful for  
two purposes: a) Very basic on-the-fly image processing on the texture. b)  
Procedural shading: Your texture matrix doesn't encode an image, but only  
per-pixel parameters as input for some formula to compute the real image during  
drawing. E.g., instead of defining a gabor patch as image or other standard  
stimulus, one could define it as a mathematical formula to be evaluated at  
draw-time. The [Screen](Screen)('SetOpenGLTexture') command allows you to create purely  
virtual textures which only consist of such a shader and some virtual size, but  
don't have any real data matrix associated with it -- all content is generated  
on the fly.  
  


###See also:
[DrawTexture](Screen-DrawTexture) [TransformTexture](Screen-TransformTexture) [BlendFunction](Screen-BlendFunction)
