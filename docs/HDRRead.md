# [HDRRead](HDRRead)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BrightSideDisplay](BrightSideDisplay)

img = [HDRRead](HDRRead)(imgfilename[, continueOnError=0][, flipit=0])  
Read a high dynamic range image file and return it as Matlab double  
matrix, suitable for use with [Screen](Screen)('MakeTexture') and friends.  
  
'imgfilename' - Filename of the HDR image file to load.  
Returns 'img' - A double precision matrix of size h x w x c where h is  
the height of the input image, w is the width and c is the number of  
color channels: 1 for luminance images, 2 for luminance images with alpha  
channel, 3 for true-color RGB images, 4 for RGB images with alpha  
channel.  
  
'continueOnError' Optional flag. If set to 1, [HDRRead](HDRRead) won't abort on  
error, but simply return an empty img matrix. Useful for probing if a  
specific file type is supported.  
  
'flipit' Optional flag: If set to 1, the loaded image is flipped upside  
down.  
  
[HDRRead](HDRRead) is a dispatcher for a collection of reading routines for  
different HDR image file formats. Currently supported are:  
  
\* Run length encoded RGBE format, read via read\_rle\_rgbe.m, extension is  
".hdr". Returns a RGB image.  
  
The reader routines are contributed code or open source / free software /  
public domain code downloaded from various locations under different, but  
GPL compatible licenses. See the help for the respective loaders for  
copyright and author information.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/HDRRead.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BrightSideDisplay/HDRRead.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BrightSideDisplay/HDRRead.m</code>
</div>

