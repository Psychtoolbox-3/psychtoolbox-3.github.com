# [moglClutBlit](moglClutBlit)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

EXPERIMENTAL - BETA QUALITY:  
  
moglClutBlit(win, src [, newclut]) -- Blit an image into window, apply CLUT.  
  
moglClutBlit copies a texture image 'src' (either made via  
src = [Screen](Screen)('MakeTexture', ...) or an offscreen window created via  
src = [Screen](Screen)('OpenOffscreenWindow', ...)) to an onscreen window 'win'.  
  
During the copy, it applies a color lookup table (clut) to the texture,  
transforming the color indices in the input texture into RGB color  
pixels according to the color lookup table.  
  
The color lookup table contains 256 rows with 3 columns. The i'th row  
contains the Red, green and blue color values to be used when an input  
pixel with colorindex i-1 is used. Column 1 = Red component, column 2 =  
Green component, column 3 = blue component.  
  
The clut will be initialized to a gray-level ramp, i.e. index 1 =  
(0,0,0), index i+1 = (i, i, i), index 256 = (255, 255, 255).  
  
### Arguments:  
  
'src' texture handle or offscreen window handle of the image to copy.  
'win' window handle of the target window.  
'newclut' The new 256 rows by 3 columns clut. If you don't provide any  
clut, the clut from a previous call will be used. Initially it is a  
graylevel ramp.  
  
Usage:  
1. Add the command "[InitializeMatlabOpenGL](InitializeMatlabOpenGL)" at the top of your script,  
before the first call to [Screen](Screen)('OpenWindow', ...). If you don't use any  
3D graphics, [InitializeMatlabOpenGL](InitializeMatlabOpenGL)([], 0, 1); will be the fastest.   
  
2. Create your color index image either as a texture, e.g., via  
src=[Screen](Screen)('MakeTexture', win, myimage), or create it as Offscreen window  
src=[Screen](Screen)('OpenOffscreenWindow', win) and draw your index colored  
stimulus into it.  
  
3. Whenever you want to change the clut and draw the image with updated  
clut, call moglClutBlit(win, src, newclut); with newclut being the new  
color lookup table.  
  
4. Call the [Screen](Screen)('[Flip](Flip)', ...) command to show the new image, drawn with  
the new clut.  
  
5. At the end of your script and before you [Screen](Screen)('[Close](Close)', win) or  
[Screen](Screen)('CloseAll'), call moglClutBlit() without parameters, so it can  
clean up after itself.  
  
See [GLSLClutAnimDemo](GLSLClutAnimDemo) for an example.  
  
Note: This function requires you to use fairly recent graphics hardware  
with support for [OpenGL](OpenGL) Pixelshaders and the [OpenGL](OpenGL) shading language  
(GLSL). It won't work on old hardware. Use of cluts for 8 bit clut  
animation is deprecated. Today, most stimuli can be generated in much more  
flexible and elegant ways using PTB-3's new drawing features and [OpenGL](OpenGL)  
capabilities.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/moglClutBlit.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/moglClutBlit.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/moglClutBlit.m</code>
</div>

