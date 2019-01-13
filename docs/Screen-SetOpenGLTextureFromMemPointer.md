# [Screen('SetOpenGLTextureFromMemPointer')](Screen-SetOpenGLTextureFromMemPointer) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[textureHandle rect] = Screen('SetOpenGLTextureFromMemPointer', windowPtr, textureHandle, imagePtr, width, height, depth [, upsidedown][, target][, glinternalformat][, gltype][, extdataformat][, specialFlags]);

DANGEROUS! C-PROGRAMMING EXPERTS ONLY! OTHERS STAY AWAY! Convert raw image data,  
provided as a pointer to a system memory buffer, into a Psychtoolbox texture.  
CAUTION: Providing wrong arguments to this subfunction will definitely crash  
Psychtoolbox and Matlab! "windowPtr" is the handle of the onscreen window to  
which the texture should be attached. 'textureHandle' is either the Psychtoolbox  
handle for an existing PTB texture that should be updated with the new raw pixel  
data, or the special value zero or [] if a completely new PTB texture should be  
created from the raw pixel data. 'imagePtr' is a C programming language (void\*)  
memory pointer that points to the start of a memory buffer with the raw image  
data. The pointer needs to be encoded in a special way. Read the source code of  
[Memorybuffer2Texture](Memorybuffer2Texture).c and [Memorybuffer2TextureDemo](Memorybuffer2TextureDemo).m for minimal examples on  
how to do this properly. [Memorybuffer2Texture](Memorybuffer2Texture).cc demonstrates the same for  
GNU/Octave. The optional parameter 'target' is the type of texture object to  
create, e.g., GL\_TEXTURE\_2D. Normally you'll just leave it out, so PTB can  
choose the optimal texture format for a system. 'width' and 'height' are the  
width and height of the image. 'depth' is the depth of the image: 1 = Input is a  
greyscale image with 1 Byte per pixel. 3 = Input is a RGB truecolor image with 3  
Bytes per pixel. 2 and 4 are like 1 and 3, but with one byte for an alpha  
(transparency) channel added. The optional flag 'upsidedown' can be set to one  
(default is zero) to create textures upside-down - inverted in vertical  
direction. 'glinternalformat', 'gltype' and 'extdataformat' are all optional. If  
you provide one of them, you'll need to provide all of them. In that case, PTB  
will create an [OpenGL](OpenGL) texture with exactly the specified internal format,  
assuming input data that is of type 'gltype' and in numeric data format  
'extdataformat'. You are completely responsible for passing properly formatted  
data. This is mostly useful for injecting high dynamic range texture images and  
other exotic texture formats.  
'specialFlags' Special optional texture flags, see help for  
[Screen](Screen)('MakeTexture').  
The function returns the textureHandle of the PTB texture and its defining  
rectangle. This routine allows external C-Code (Mex- or Oct-Files) to inject raw  
image data as a texture into PTB.   


###See also:
[SetOpenGLTexture](Screen-SetOpenGLTexture) [MakeTexture](Screen-MakeTexture) 
