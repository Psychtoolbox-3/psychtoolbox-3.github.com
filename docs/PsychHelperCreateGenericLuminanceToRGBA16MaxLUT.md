# [PsychHelperCreateGenericLuminanceToRGBA16MaxLUT](PsychHelperCreateGenericLuminanceToRGBA16MaxLUT)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

luttex = [PsychHelperCreateGenericLuminanceToRGBA16MaxLUT](PsychHelperCreateGenericLuminanceToRGBA16MaxLUT)(lut, targetBpc, win);  
  
Helper function for [PsychImaging](PsychImaging)() - Don't call from usercode!  
  
Used by [PsychImaging](PsychImaging)(....,'EnableGenericHighPrecisionLuminanceOutput', lut);  
Converts a uint16 luminance -\> RGB8/10/16 or RGBA8/10/16 LUT as provided in  
the 3- or 4 rows by n columns matrix 'lut' into an equivalent RGBA8/10/16  
lookup table texture, then returns the texture handle to the calling routine.  
  
'lut' = 3 rows by nslots columns uint8 matrix for LUT's that map the  
input luminance value range [0.0 - 1.0] to the integral 0 - nslots range,  
then lookup the corresponding RGB8/10/16 output pixel in the lut. If 'lut' has  
4 rows, then the 4th row encodes alpha-channel - This is only useful for  
debugging, as teh alpha channel can't be output to the external device.  
  
### Implementation details:  
  
The lut texture is built as a 256x256 2D rectangle texture, allowing for  
luts with up to 2^16 luminance slots that work on all supported graphics  
hardware. One could extend the size of the texture to up to 8192x8192 on  
latest hardware, allowing for up to 2^26 bits, but that is likely not  
that useful, given that internal GPU precision is restricted to 23 bits  
(floating point single precision) and there doesn't exist a single output  
device with more than 16 bits of output resolution anyway.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/PsychHelperCreateGenericLuminanceToRGBA16MaxLUT.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/PsychHelperCreateGenericLuminanceToRGBA16MaxLUT.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/PsychHelperCreateGenericLuminanceToRGBA16MaxLUT.m</code>
</div>

