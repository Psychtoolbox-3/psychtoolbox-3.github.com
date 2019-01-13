# [Screen('SetOpenGLTexture')](Screen-SetOpenGLTexture) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[textureHandle rect] = Screen('SetOpenGLTexture', windowPtr, textureHandle, glTexid, target [, glWidth] [, glHeight] [, glDepth] [, textureShader][, specialFlags]);

Provides information about an external [OpenGL](OpenGL) texture to make it acessible for  
PTB as PTB texture."windowPtr" is the handle of the onscreen window to which  
texture should be attached. 'textureHandle' is either the Psychtoolbox handle  
for an existing PTB texture, or the special value zero or [] if a completely new  
PTB texture should be created for this [OpenGL](OpenGL) texture. glTexid is the [OpenGL](OpenGL)  
texture id of a valid [OpenGL](OpenGL) texture object. 'target' is the type of texture  
(e.g., GL\_TEXTURE\_2D) Optionally you can pass in the intended width and height  
as well as pixeldepth of the texture if they should be different from the values  
that PTB can autodetect from the given texture object.  
'textureShader' - optional: If you provide the handle of an [OpenGL](OpenGL) GLSL shader  
program, then this shader program will be executed (bound) during drawing of  
this texture via the [Screen](Screen)('DrawTexture',...); command -- The normal texture  
drawing operation is replaced by your customized algorithm. This is useful for  
two purposes: a) Very basic on-the-fly image processing on the texture. b)  
Procedural shading: Your texture matrix doesn't encode an image, but only  
per-pixel parameters is input for some formula to compute the real image during  
drawing. E.g., instead of defining a gabor patch as image or other standard  
stimulus, one could define it as a mathematical formula to be evaluated at  
draw-time. The [Screen](Screen)('SetOpenGLTexture') command allows you to create purely  
virtual textures, that only consist of such a shader and some virtual size, but  
don't have any real data matrix associated with it -- all content is generated  
on the fly. Create such a texture by providing a textureShader that will  
algorithmically generate the texture content, and the virtual size of the  
texture in glWidth, glHeight and glDepth, but set the glTexid texture handle to  
zero.  
'specialFlags' Special optional texture flags, see help for  
[Screen](Screen)('MakeTexture').  
The function returns (optionally) the textureHandle of the PTB texture and its  
defining rectangle. This routine allows external [OpenGL](OpenGL) code to inject textures  
into PTB for use with it. For more info about [OpenGL](OpenGL) textures, read an [OpenGL](OpenGL)  
book.   


###See also:
[GetOpenGLTexture](Screen-GetOpenGLTexture)
