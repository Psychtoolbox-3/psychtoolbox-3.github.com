# [SimpleHDRDemo](SimpleHDRDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[SimpleHDRDemo](SimpleHDRDemo)([imfilename]) - Load and show a high dynamic range (HDR) image  
on a compatible HDR display setup.  
  
Press any key to terminate the demo.  
  
'imfilename' - Optional filename of the HDR image to load. This will load  
a standard HDR demo image bundled with Matlab, if omitted, or abort if  
the default demo image is missing. Currently only '.hdr' RGBE images are  
supported.  
  
See "help [PsychHDR](PsychHDR)" for system requirements and setup instructions for HDR  
display. Once these are satisfied, converting a standard Psychtoolbox visual  
stimulation script into a HDR script is straightforward, as shown in this simple  
demo. Modify your scripts in the following manner:  
  
1. Use (as most minimal setup) the sequence ...  
  
   [PsychImaging](PsychImaging)('PrepareConfiguration');  
   [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableHDR');  
   win = [PsychImaging](PsychImaging)('OpenWindow', screenid);  
  
   ... instead of ...  
  
   win = [Screen](Screen)('OpenWindow', screenid);  
  
   ... to open a fullscreen onscreen window on a HDR capable display device,  
   which is attached to a HDR capable graphics card.  
  
2. Use [HDRRead](HDRRead)(imfilename) instead of imread(imfilename) to load HDR  
   image files as double() precision matrices.  
  
3. Optional: Set the optional 'floatprecision' flag of [Screen](Screen)('MakeTexture', ...)  
   to 1 or 2 to enforce creation of floating point precision HDR textures  
   of a specific precision from your image matrix.  
  
   By default, 'floatprecision' will be selected as 2 for single  
   precision float fp32 format, which is the maximum precision for  
   processing and displaying HDR images.  
  
  
See the section 'EnableHDR' of "help [PsychImaging](PsychImaging)" for more optional parameters  
to pass to [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableHDR'); for customizing the  
HDR display mode. See "help [PsychHDR](PsychHDR)" for more helper subfunctions to customize  
HDR display further at runtime, once the fullscreen onscreen HDR display window  
has been opened and initially set up by [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableHDR').  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/SimpleHDRDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/SimpleHDRDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/SimpleHDRDemo.m</code>
</div>

