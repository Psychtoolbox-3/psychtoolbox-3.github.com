# [kPsychEnableSRGBRendering](kPsychEnableSRGBRendering)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychEnableSRGBRendering  
  
Return a flag that you can pass to the 'imagingmode' parameter of  
[Screen](Screen)('OpenWindow'). If this kPsychEnableSRGBRendering flag is  
given then rendering to the framebuffer will happen in sRGB format  
if the target framebuffer supports this, ie. is in sRGB color buffer  
format.  
  
The sRGB color space is based on typical (non-linear) monitor  
characteristics expected in a dimly lit office.  It has been  
standardized by the International Electrotechnical Commission (IEC)  
as IEC 61966-2-1. The sRGB color space roughly corresponds to 2.2  
gamma correction.  
  
### See this spec for more details:  
  
https://www.khronos.org/registry/[OpenGL](OpenGL)/extensions/ARB/ARB\_framebuffer\_sRGB.txt  
  
In general, only RGBA8 framebuffer formats are sRGB capable, as  
typical GPU's do not implement sRGB on other formats, and for  
floating point framebuffers, sRGB encoding would be pointless,  
as they provide already a non-linear format with much more precision,  
so no need for sRGB style compression.  
  
Given that [Screen](Screen)() does not explicitely request sRGB system framebuffers,  
this flag will only apply to output (sink) FBO's when the imaging pipeline  
is active, and there only if an external sink texture is passed in by some  
external client, ie. the kPsychUseExternalSinkTextures flag is given as well.  
  
The only known potential client of this is currently the Oculus VR runtime  
compositor, which wants to process sRGB RGBA8 textures as input, unless you  
choose half-float textures.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychEnableSRGBRendering.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychEnableSRGBRendering.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychEnableSRGBRendering.m</code>
</div>

