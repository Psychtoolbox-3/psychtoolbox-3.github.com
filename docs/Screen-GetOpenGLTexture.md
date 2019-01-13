# [Screen('GetOpenGLTexture')](Screen-GetOpenGLTexture) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[ gltexid gltextarget texcoord_u texcoord_v ] =Screen('GetOpenGLTexture', windowPtr, textureHandle [, x][, y]);

Returns information about the [OpenGL](OpenGL) texture corresponding to a Psychtoolbox  
texture. "windowPtr" is the handle of the onscreen window for which texture  
should be returned. 'textureHandle' is the Psychtoolbox handle for the requested  
texture. Optionally you can pass in Psychtoolbox texture coordinates (x,y) and  
get them mapped to the proper [OpenGL](OpenGL) texture coordinates. Return values:  
'gltexid' [OpenGL](OpenGL) texture id for binding the texture. 'gltextarget' type of  
[OpenGL](OpenGL) texture target to use. 'texcoord\_u' and 'texcoord\_v' [OpenGL](OpenGL) texture  
coordinates corresponding to 'x' and 'y'. Immediately after calling this  
routine, the proper [OpenGL](OpenGL) rendering context for the requested texture is  
activated for use. Example of usage: glBindTexture(gltextarget, gltexid); //  
Activate and bind req. texture. glTexCoord2d(texcoord\_u, texcoord\_v); // Assign  
texture pixel (x,y) to next vertex. For more info, read an [OpenGL](OpenGL) book.   


###See also:
[SetOpenGLTexture](Screen-SetOpenGLTexture)
