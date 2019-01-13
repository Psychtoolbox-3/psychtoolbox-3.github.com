# [Screen('DrawTexture')](Screen-DrawTexture) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

Screen('DrawTexture', windowPointer, texturePointer [,sourceRect] [,destinationRect] [,rotationAngle] [, filterMode] [, globalAlpha] [, modulateColor] [, textureShader] [, specialFlags] [, auxParameters]);

Draw the texture specified via 'texturePointer' into the target window specified  
via 'windowPointer'. In the the OS X Psychtoolbox textures replace offscreen  
windows for fast drawing of images during animation.'sourceRect' specifies a  
rectangular subpart of the texture to be drawn (Defaults to full texture).  
'destinationRect' defines the rectangular subpart of the window where the  
texture should be drawn. This defaultsto centered on the screen. 'rotationAngle'  
Specifies a rotation angle in degree for rotated drawing of the texture  
(Defaults to 0 deg. = upright). 'filterMode' How to compute the pixel color  
values when the texture is drawn magnified, minified or drawn shifted, e.g., if  
sourceRect and destinationRect do not have the same size or if sourceRect  
specifies fractional pixel values. 0 = Nearest neighbour filtering, 1 = Bilinear  
filtering - this is the default. Values 2 or 3 select use of [OpenGL](OpenGL) mip-mapping  
for improved quality: 2 = Bilinear filtering for nearest mipmap level, 3 =  
Trilinear filtering across mipmap levels, 4 = Nearest neighbour filtering for  
nearest mipmap level, 5 = nearest neighbour filtering with linear interpolation  
between mipmap levels. Mipmap filtering is only supported for GL\_TEXTURE\_2D  
textures (see description of 'specialFlags' flag 1 below). A negative filterMode  
value will also use mip-mapping for fast drawing of blurred textures if the  
GL\_TEXTURE\_2D format is used: Mip-maps are essentially image resolution  
pyramids, the filterMode value selects a specific layer in that pyramid. A value  
of -1 draws the highest resolution layer, a value of -2 draws a half-resolution  
layer, a value of -3 draws a quarter resolution layer and so on. Each layer has  
half the resolution of the preceeding layer. This allows for very fast drawing  
of blurred or low-pass filtered images, e.g., for gaze-contingent displays.  
However, the filter function for downsampling is system dependent and may vary  
across graphics cards, although a box-filter is the most common type. If you  
need a well defined filter function, use a custom written GLSL shader instead,  
so you have full control over the mathematical properties of the downsampling  
function. This would incur a performance penalty.  
'globalAlpha' A global alpha transparency value to apply to the whole texture  
for blending. Range is 0 = fully transparent to 1 = fully opaque, defaults to  
one. If both, an alpha-channel and globalAlpha are provided, then the final  
alpha is the product of both values. 'modulateColor', if provided, overrides the  
'globalAlpha' value. If 'modulateColor' is specified, the 'globalAlpha' value  
will be ignored. 'modulateColor' will be a global color that gets applied to the  
texture as a whole, i.e., it modulates each color channel. E.g., modulateColor =  
[128 255 0] would leave the green- and alpha-channel untouched, but it would  
multiply the blue channel with 0 - set it to zero blue intensity, and it would  
multiply each texel in the red channel by 128/255 - reduce its intensity to 50%.  
The most interesting application of 'modulateColor' is drawing of arbitrary  
complex shapes of selectable color: Simply generate an all-white luminance  
texture of arbitrary shape, possibly with alpha channel, then draw it with  
'modulateColor' set to the wanted color and global alpha value.  
'textureShader' (optional): If you provide a valid handle of a GLSL shader, this  
shader will be applied to the texture during drawing. If the texture already has  
a shader assigned (via [Screen](Screen)('MakeTexture') or automatically by PTB for some  
reason), then the shader provided here as 'textureShader' will silently override  
the shader assigned earlier. Application of shaders this way is mostly useful  
for application of simple single-pass image processing operations to a texture,  
e.g., a simple blur or a deinterlacing operation for a video texture. If you  
intend to use this texture multiple times or if you need more complex image  
processing, e.g., multi-pass operations, better use the  
[Screen](Screen)('TransformTexture') command. It allows for complex operations to be  
applied and is more flexible.  
'specialFlags' optional argument: Allows to pass a couple of special flags to  
influence the drawing. The flags can be combined by mor() ing them together. A  
value of kPsychUseTextureMatrixForRotation will use a different mode of  
operation for drawing of rotated textures, where the drawn 'dstRect' texture  
rectangle is always upright, but texels are retrieved at rotated positions, as  
if the 'srcRect' rectangle would be rotated. If you set a value of  
kPsychDontDoRotation then the rotation angle will not be used to rotate the  
texture. Instead it will be passed to a bount texture shader (if any), which is  
free to interpret the 'rotationAngle' parameters is it wants - e.g., to  
implement custom texture rotation.  
  
'auxParameters' optional argument: If this is set as a vector with at least 4  
components, and a multiple of four components, then these values are passed to a  
shader (if any is bound) as 'auxParameter0....n'. The current implementation  
supports at most 32 values per draw call. This is mostly useful when drawing  
procedural textures if one needs to pass more additional parameters to define  
the texture than can fit into other parameter fields. See 'help  
ProceduralShadingAPI' for more info.   
  
If you want to draw many textures to the same onscreen- or offscreen window, use  
the function [Screen](Screen)('DrawTextures'). It accepts the same arguments as this  
function, but is optimized to draw many textures in one call.  


###See also:
[MakeTexture](Screen-MakeTexture) [DrawTexture](Screen-DrawTexture) [DrawTextures](Screen-DrawTextures)
