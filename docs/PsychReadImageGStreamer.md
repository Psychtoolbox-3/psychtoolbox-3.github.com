# [PsychReadImageGStreamer](PsychReadImageGStreamer)
##### >[Psychtoolbox](Psychtoolbox)>[PsychFiles](PsychFiles)

img = [PsychReadImageGStreamer](PsychReadImageGStreamer)(imagefile, win [, uselowprecision=0])  
  
Caution: Experimental implementation - not much tested yet. Here be dragons!  
  
Reads an image file (or URL) by (ab)using [[GStreamer](GStreamer)][(GStreamer]((GStreamer))'s ability to read image  
files as if they were movies. Returns double() or uint8() RGB image matrix  
with decoded image in 'img' if the image file format is supported by [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)).  
  
This is mostly meant as a fallback for reading exotic image files unsupported  
by imread() or HDR files unsupported by our other HDR reading routines. In the  
latter case, usefulness might be limited as of [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) 1.18, as [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))  
only supports unorm value range with up to 16 bpc for some formats, but not  
the out-of-unorm float range often needed for HDR imaging data. Might still be  
useful though for some high-precision unorm range formats.  
  
'imagefile' Name or URL of the image file to load.  
  
'win' Onscreen window handle, as we abuse [Screen](Screen)()'s movie playback functions  
for this, and they always need an onscreen window handle to work.  
  
'uselowprecision' Optional: If set to 1, return uint8() data RGB8, otherwise  
return high precision double() matrix which contains single precision float  
RGB image data, enough to cover 16 bpc unorm data and up to 32 bpc float data.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychFiles/PsychReadImageGStreamer.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychFiles/PsychReadImageGStreamer.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychFiles/PsychReadImageGStreamer.m</code>
</div>

