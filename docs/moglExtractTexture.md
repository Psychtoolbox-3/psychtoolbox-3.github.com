# [moglExtractTexture](moglExtractTexture)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

moglExtractTexture(cmd [, arg1][, arg2][, ...]) - "MOGL Video texture extraction"  
  
  
The algorithm makes heavy use of GPU based image processing for maximum  
speed, so it needs at least [NVidia](NVidia) Geforce 6000 series or ATI Radeon  
X1000 series graphics hardware (and any later models or equivalent  
hardware) to work. It also needs the PTB imaging pipeline enabled, at  
least fast offscreen window support. You do this, e.g., by replacing a  
call to ...  
  
[win, winRect] = [Screen](Screen)('OpenWindow', screenid, 0);  
  
... with a call sequence like this ...  
  
[PsychImaging](PsychImaging)('PrepareConfiguration');  
[PsychImaging](PsychImaging)('AddTask', 'General', 'UseFastOffscreenWindows');  
[win , winRect] = [PsychImaging](PsychImaging)('OpenWindow', screenid, 0);  
  
  
  
Subcommands, their syntax & meaning:  
====================================  
  
[oldflag, oldgain] = moglExtractTexture('DebugFlag', flag [, debugGain]);  
- Set debug flag to value 'flag'. Default is zero. Non-zero values enable  
different visualizations that may aid debugging non-working setups. 1 =  
Show silhouette buffer, 2 = Show trackbuffer, 3 = Show extracted texture.  
A setting of -1 shows the real rendered image. A value of -2 disables any  
kind of textual warnings.  
  
The optional 'debugGain' parameter must be a 4 component [R G B A] color  
vector with modulation gains for the drawn "debug images" - simply to  
scale each color channel in intensity to allow for display of values  
outside the standard displayable range between zero and one.  
  
  
context = moglExtractTexture('CreateContext', window, rect, texCoordMin, texCoordMax, texResolution [,zThreshold=Off]);   
- Create a "rendercontext" for a single 3D object. Returns a 'context'  
handle to it which needs to be passed in to all other functions as  
reference. All following parameters are required and don't have any  
defaults:  
  
'window' Handle of masterwindow - The onscreen window used for rendering.  
This is not neccessarily the window to which final stimulus will be drawn  
to, but it is needed as a "parent" for all ressources.  
  
'rect' A Psychtoolbox rectangle [left top right bottom] that describes  
the size and shape of the input video texture. This rect must have the  
same size as the input video image textures -- Lots of internal  
calculations depend on this geometry spec!  
  
'texCoordMin' Two element vector which contains the minimum texture  
coordinate values contained in the 3D scene for x- resp. y-direction.  
  
'texCoordMax' Two element vector which contains the maximum texture  
coordinate values contained in the 3D scene for x- resp. y-direction.  
  
'texResolution' Two element vector which contains the internal resolution  
for x- resp. y-direction of the 3D object surface. Higher values mean finer  
resolution and less aliasing, but also higher storage requirements and  
longer processing times. This defines the size of returned extracted  
textures.  
  
'zThreshold' Optional zThreshold for occlusion test: By default, it is  
10.0 ie. occlusion test disabled. A value between 0.0 and 1.0 will enable  
occlusion testing -- Texels that would correspond to occluded surface patches are  
not extracted. Small numbers (close to zero) make the test more sensitive but  
can cause artifacts due to internal numeric roundoff errors. Bigger  
numbers (closer to one) make it more robust but less powerful. The  
"sweet-spot" depends on your hardware and 3D scene. Empirically a setting  
of 0.0001 is a good value for ATI Radeon X1000 series hardware.  
The default setting (bigger than 1.0) will disable occlusion test --  
"Hidden texels" are not ignored, but updated with bogus extracted texture.  
  
  
context = moglExtractTexture('SetRenderCallback', context, callbackEvalString);  
- Define the 'eval' string for this context to be used as rendercallback.  
Pass in a Matlab command string (for evaluation via eval() function in the  
Workspace of the calling function). This string is called/executed during  
each 'Update' cycle. It has to contain the code that performs the actual  
rendering of the 3D scene or object.  
  
The called rendering code \*must not\* glClear() the framebuffer or mess  
around with alpha-blending state or depth-buffer/depth-test settings, nor  
should it bind any shaders! It makes sense to disable any kind of  
lighting or texture mapping, as no photorealistic image is rendered, so  
it would be a waste of computation time.  
  
  
context = moglExtractTexture('DestroyContext', context);  
- Destroy a processing context, release all of its ressources.  
  
  
[texBuffer, texId, texTarget] = moglExtractTexture('Extract', context, inputTexture [, newTexture = 0]);  
- Perform an 'Extract' cycle for given context. A new "3D frame" is rendered  
via the rendercallback function, then analysed, to provide the 3D surface  
geometry and occlusion info and mapping for texture extraction. This info  
is then used to extract pixel color values from the given video input  
texture 'inputTexture' and the final extracted texturemap is stored  
inside an internal texture buffer. A handle to that internal buffer  
'texBuffer' is returned. The handle is owned by this function! You should  
not close or otherwise mess with the provided buffer. You can read the  
final texture from it, acquire a temporary [OpenGL](OpenGL) texture handle to it  
for texture mapping, etc. You are even allowed to perform destructive  
write informations on the buffer to change its pixel content. But do not  
destory and reallocate the buffer, change its size, number of layers,  
resolution or any other property! For your convenience, 'texId' and  
'texTarget' also provide standard [OpenGL](OpenGL) handles to texture id and  
target, associated with 'texBuffer'.  
  
Alternatively you can set the optional flag 'newTexture' to a value of 1.  
In that case, a new extracted texture 'texBuffer' is returned and you own  
this texture, ie., you can do with it whatever you want and you are  
responsible for releasing the texture via [Screen](Screen)('[Close](Close)', texBuffer);  
once you are done with it.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/moglExtractTexture.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/moglExtractTexture.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/moglExtractTexture.m</code>
</div>

