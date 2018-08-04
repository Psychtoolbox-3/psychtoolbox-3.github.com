# [moglFDF](moglFDF)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

moglFDF(cmd [, arg1][, arg2][, ...]) - "MOGL [FormlessDotFields](FormlessDotFields)"  
  
Implementation of Sheinberg et al. inspired random dot structure from motion  
rendering. This routine is a fast implementation of "Formless dot field  
structure-from-motion stimuli". It is based on - and very similar in  
behaviour, although not identical in implementation - the algorithm  
proposed by Jedediah M. Singer and David L. Sheinberg in their  
Journal of Vision paper "A method for the real-time rendering of  
formless dot field structure-from-motion stimuli" (Journal of Vision, 8,  
1-8)  
  
This algorithm takes the idea of the above mentioned paper and pushes it  
one step further by moving nearly all stimulus computation onto the GPU.  
  
All compute intense tasks are carried out by vertex- and fragment-shaders  
on the GPU and all heavy data structures are stored within the GPU's fast  
local VRAM memory, reducing the amount of communication between host  
system and graphics card to an absolute minimum. The Matlab code on the  
CPU only controls the flow of operations on the GPU and generates a  
matrix with random numbers to update the sample distribution. This should  
provide a significant speedup beyond what the Singer et al. algorithm  
achieves, at least for complex and demanding stimuli.  
  
  
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
  
  
A minimal example of how to use moglFDF to render a "dotfield"  
representation of a rotating 3D sphere can be found in the [FDFDemo](FDFDemo).m  
file.  
  
  
Subcommands, their syntax & meaning:  
====================================  
  
[oldflag, oldgain] = moglFDF('DebugFlag', flag [, debugGain]);  
- Set debug flag to value 'flag'. Default is zero. Non-zero values enable  
different visualizations that may aid debugging non-working setups.  
1 = Show silhouette buffer, 2 = Show trackbuffer, 3 = Show random noise  
sampling texture, 4 = Show sampleBuffer, 5 = Show [FGDots](FGDots) buffer. A  
setting of -1 shows the real rendered image, instead of the random dot  
visualization. A value of -2 disables any kind of textual warnings.  
  
The optional 'debugGain' parameter must be a 4 component [R G B A] color  
vector with modulation gains for the drawn "debug images" - simply to  
scale each color channel in intensity to allow for display of values  
outside the standard displayable range between zero and one.  
  
  
context = moglFDF('CreateContext', window, rect, texCoordMin, texCoordMax, texResolution, maxFGDots, maxBGDots, dotLifetime [,zThreshold=Off] [,[BGSilhouetteAcceptanceProbability](BGSilhouetteAcceptanceProbability)=0.0]);   
- Create a "rendercontext" for a single 3D object. Returns a 'context'  
handle to it which needs to be passed in to all other functions as  
reference. All following parameters are required and don't have any  
defaults:  
  
'window' Handle of masterwindow - The onscreen window used for rendering.  
This is not neccessarily the window to which final stimulus will be drawn  
to, but it is needed as a "parent" for all ressources.  
  
'rect' A Psychtoolbox rectangle [left top right bottom] that describes  
the size and shape of the final stimulus window. This rect must have the  
same size as the 3D window and final stimulus window -- Lots of internal  
calculations depend on this geometry spec.  
  
'texCoordMin' Two element vector which contains the minimum texture  
coordinate values contained in the 3D scene for x- resp. y-direction.  
  
'texCoordMax' Two element vector which contains the maximum texture  
coordinate values contained in the 3D scene for x- resp. y-direction.  
  
'texResolution' Two element vector which contains the internal resolution  
for x- resp. y-direction of the 3D object surface. Higher values mean finer  
resolution and less aliasing, but also higher storage requirements and  
longer processing times.  
  
'maxFGDots' Maximum number of foreground (object shape) dots to use for  
random shape sampling. This must be an integral multiple of  
'dotLifetime'. If it isn't, it will get adjusted to become an integral  
multiple.  
  
'maxBGDots' Maximum number of background dots to use for random background  
sampling. This must be an integral multiple of 'dotLifetime'. If it  
isn't, it will get adjusted to become an integral multiple. If you don't  
want to have structure cues in your stimulus, you should set 'maxBGDots'  
equal to 'maxFGDots' to keep overall dot density on the display constant.  
  
'dotLifetime' Lifetime of each foreground- or background dot in 'Update'  
cycles. Each dot is replace by a new random sample after that many  
invocations of the 'Update' function.  
  
'zThreshold' Optional zThreshold for occlusion test: By default, it is  
10.0 ie. occlusion test disabled. A value between 0.0 and 1.0 will enable  
occlusion testing -- Dots that would correspond to occluded surfaces are  
not drawn. Small numbers (close to zero) make the test more sensitive but  
can cause artifacts due to internal numeric roundoff errors. Bigger  
numbers (closer to one) make it more robust but less powerful. The  
"sweet-spot" depends on your hardware and 3D scene. Empirically a setting  
of 0.0001 is a good value for ATI Radeon X1000 series hardware.  
The default setting (bigger than 1.0) will disable occlusion test --  
"Hidden dots" are not hidden, but drawn.  
  
'BGSilhouetteAcceptanceProbability' Optional [BGSilhouetteAcceptanceProbability](BGSilhouetteAcceptanceProbability)  
This is the probability with which a dot from the "background distribution"   
will be drawn if it is actually located in the area of the objects  
silhouette. A value of 0.0 (which is the default) will not draw any  
background dots within the objects silhouette. Values between 0 and 1  
correspond to acceptance probabilities between 0% and 100%. If you want  
to keep the overall dot density of foreground dots and background dots  
constant (in order to not provide segmentation cues based on structure),  
you should set the 'maxFGDots' parameter like this:  
  
maxFGDots = (1 - [BGSilhouetteAcceptanceProbability)](BGSilhouetteAcceptanceProbability)) \* maxBGDots;  
  
  
context = moglFDF('SetRenderCallback', context, callbackEvalString);  
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
  
  
context = moglFDF('ReinitContext', context, rect, texCoordMin, texCoordMax, texResolution, maxFGDots, maxBGDots, dotLifetime [,zThreshold=Off] [,[BGSilhouetteAcceptanceProbability](BGSilhouetteAcceptanceProbability)=0.0]);   
- Reinitialize an already existing context with new stimulus parameters.  
The parameters are identical to the ones in 'CreateContext', except for  
the first one: You don't pass a windowhandle of a parent window, as this  
stays the same for the reinitialized context. Instead you pass the handle  
of the 'context' to reinitialize.  
  
'ReinitContext' is the same as a sequence of 'DestroyContext', followed  
by a new 'CreateContext', except that it is optimized for speed --  
Reinitialization with new parameters is typically at least 3 times faster  
than a full destroy & recreate operation.  
  
  
context = moglFDF('DestroyContext', context);  
- Destroy a processing context, release all of its ressources.  
  
  
context = moglFDF('ResetState', context);  
- Reset processing contexts state to initial state, just as if it was  
just created. Useful at start of a new trial. Another way to start a new  
trial, but with a full distribution already initialized, is to use the  
moglFDF('Update') call with the 'instantOn' flag set to 1 for the first  
iteration of your stimulus loop, instead of the default of zero.  
  
  
context = moglFDF('SetColorTexture', context, textureId, textureTarget);  
- Assign a regular color texture map with handle 'textureId' and texture  
mapping target 'textureTarget' to 'context'. This will enable assignment  
of colors to drawn 2D dots (in moglFDF('Render',...);) and fetch the  
relevant per-dot colors from the assigned texture map 'textureId'.  
  
Assigning an empty or negative textureId will disable texture mapping.  
Texture mapping is disabled by default, i.e. at context creation time.  
  
  
context = moglFDF('SetDrawShader', context, fgShaderId [, bgShaderId] [, needSprites]);  
- Assign a GLSL shader with handle 'fgShaderId' during 2D drawing of  
foreground dots in moglFDF('Render',...); Passing a 'fgShaderId' which is  
empty or negative disables shading. Shading is disabled by default.  
  
The optional 'bgShaderId' assigns potential shaders for drawing of  
background dots.  
  
The optional flag 'needSprites' if set to 1, will enable generation of  
point-sprite texture coordinates on texture unit 1 while using a shader  
with point-smoothing enabled. A setting of 0 disables point sprites.  
Point sprites plus special code within your drawing fragment shader are  
needed if you want to draw nicely anti-aliased dots on [GPUs](GPUs) that don't  
support simultaneous use of fragment shaders and anti-aliased dots. On  
such systems you can roll your own anti-aliasing via point-sprites.  
Please note that almost all consumer class GPU's don't support  
anti-aliased dots in conjunction with fragment shaders.  
  
  
context = moglFDF('Update', context [, instantOn=0]);  
- Perform an 'update' cycle for given context. A new "3D frame" is rendered  
via the rendercallback function, then analysed, resampled etc. to create  
a new complete distribution of 2D random dots, ready for drawing or  
readback. If the optional 'instantOn' flag is provided and non-zero, then  
the whole distribution is generated at once for a quick start at the  
beginning of a new trial, otherwise only one batch of samples is updated.  
By default, only one batch is updated, as required for the algorithm to  
work.  
  
  
context = moglFDF('Render', context [, targetWindow] [, drawSpec=[1,1]]);  
- Render current 2D random dot cloud (as defined by processing of last  
'Update' call) quickly and efficiently into window 'targetWindow'.  
'targetWindow' can be any onscreen- or offscreen window and is allowed to  
change at each invocation of 'Render'. By default, the 'window' from the  
'CreateContext' call is used.  
  
'drawSpec' is an optional two-element vector to select if only foreground  
dots should be rendered [1 0], only background dots should be rendered [0 1],  
or both [1 1] -- which is the default.  
  
Before calling 'Render' you can define dot sizes, colors, alpha-blending  
state, texture coordinates, anti-aliasing settings, or define texture  
mapping, point-sprite modes or texture mapping setups however you like.  
The internal 'Render' routine just defines 2D point locations, then  
invokes the render op.  
  
  
[xyFGdots, xyBGdots, uvFGdots] = moglFDF('GetResults', context); - Returns a 2 row  
by n columns vector of all random dot positions, for processing within  
Matlab/Octave. Row 1 is x-locations, Row 2 is y-locations of dots, each  
column defines one dot. The 'xyFGDots' contains all foreground dots which  
define the object, whereas the 'xyBGdots' vector contains the background  
dots. These vectors are suitable for direct drawing via  
[Screen](Screen)('DrawDots'); However, invocation of moglFDF('Render',...); is a  
more efficient method of rendering these dot fields, unless you have very  
special needs.  
  
The optional 'uvFGdots' argument returns 2D texture coordinates as  
assigned to the rendered 3D object.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/moglFDF.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/moglFDF.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/moglFDF.m</code>
</div>

