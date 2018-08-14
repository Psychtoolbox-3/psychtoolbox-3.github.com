# [SimpleHDRDemo](SimpleHDRDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BrightSideDisplay](BrightSideDisplay)

[SimpleHDRDemo](SimpleHDRDemo)([imfilename][, dummymode][, sf]) -- Load and show a high dynamic range image  
on the [BrightSide](BrightSide) Technologies High Dynamic Range display device.  
  
'imfilename' - Filename of the HDR image to load. Will load our standard  
low-dynamic range 'konijntjes' if 'imfilename' is omitted.  
  
'dummymode' - If set to 1 we only run in emulation mode without use of  
the HDR device or [BrightSide](BrightSide) core library.  
  
'sf' - Scaling factor to apply.  
  
Btw. you can find lot's of nice free HDR images by Googling on the  
internet!  
  
Except for buying and installing the display device and control  
libraries, usage with Psychtoolbox is pretty straightforward. Modify your  
scripts in the following manner:  
  
1. Use [BrightSideHDR](BrightSideHDR)('OpenWindow', ...) instead of [Screen](Screen)('OpenWindow',  
...) -- Will perform all additional display setup work for you.  
  
2. Use [HDRRead](HDRRead)(imfilename) instead of imread(imfilename) to load HDR  
image files as Matlab matrices.  
  
3. Set the 'floatprecision' flag of [Screen](Screen)('MakeTexture', ...) to 1 or 2  
to enforce creation of HDR textures from your image matrix.  
  
4. Optionally you can use the [Screen](Screen)('ColorRange', ...) command to  
upscale or downscale color values for normal 2D drawing commands. This  
won't affect drawing of textures.  
  
5. Optionally you can use fragment shaders to perform on-the-fly image  
processing when drawing an image, e.g., gamma correction, scaling, color  
conversion, tone-mapping. See the more advanced demos on how to do this.  
  
History:  
Written 2006 by Mario Kleiner - MPI for Biological Cybernetics, Tuebingen, Germany  
and Oguz Ahmet Akyuz - Department of Computer Science, University of Central Florida.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/SimpleHDRDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/SimpleHDRDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BrightSideDisplay/SimpleHDRDemo.m</code>
</div>

