# [PsychHelperCreateARGB2101010RemapCLUT](PsychHelperCreateARGB2101010RemapCLUT)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

remapCLUTId = [PsychHelperCreateARGB2101010RemapCLUT](PsychHelperCreateARGB2101010RemapCLUT);  
  
Helper function for Psychtoolbox imaging pipeline, called by  
[PsychImaging](PsychImaging)(), not meant to be called by normal user code!  
  
Build a 3 rows by 1024 texels RGBA8 lookup texture for mapping HDR RGB  
pixel values in range 0-1023 (ie. 10 bpc resolution) to RGBA8 framebuffer  
pixels which will be suitable to drive a ARGB2101010 framebuffer scanout  
engine (CRTC). If a graphics cards framebuffer scanout engine CRTC is  
configured for 2101010 10 bpc framebuffer mode, this will make sure that  
HDR pixel data is shown properly onscreen.  
  
This texture is used as CLUT texture for the  
[RGBMultiLUTLookupCombine](RGBMultiLUTLookupCombine)\_FormattingShader.frag.txt in the final output  
formatting chain of the imaging pipeline.  
  
The expected pixel layout in 10bpc mode is: ARGB2101010, ie.:  
A2R10G10B10 -- That's how a 32 bit pixel is interpreted for video  
scanout. However the [OpenGL](OpenGL) system on all current OS with standard  
drivers can only output A8R8G8B8 formatted pixels. We solve this via the  
imaging pipeline: [Screen](Screen)() and [OpenGL](OpenGL) drawing ops go to the imaging  
pipelines virtual framebuffer with 16bpc float or 32 bpc float precision.  
At [Flip](Flip) time, our shader remaps that 0.0 - 1.0 values to the range 0-1023  
ie. 10 bpc, then uses the CLUT texture created with this function to  
lookup corresponding ARGB8 color tuples for the framebuffer, combines  
them into a single ARGB8 tuple by addition (logical OR), then writes that  
ARGB tuple to the framebuffer. At display scanout time, the CRTC's will  
find 32 bit pixels properly formatted for ARGB2101010 scanout.  
  
History:  
01/13/08  Written (MK).  
08/29/11  Add caching for LUT in mat file to speed this up a bit (MK).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/PsychHelperCreateARGB2101010RemapCLUT.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/PsychHelperCreateARGB2101010RemapCLUT.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/PsychHelperCreateARGB2101010RemapCLUT.m</code>
</div>

