# [SimpleHDRLinuxStereoDemo](SimpleHDRLinuxStereoDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[SimpleHDRLinuxStereoDemo](SimpleHDRLinuxStereoDemo)([imfilename]) - Load and show a HDR image on a compatible  
HDR stereo display setup.  
  
Press any key to terminate the demo.  
  
'imfilename' - Optional filename of the HDR image to load. This will load  
a standard HDR demo image bundled with Matlab, if omitted, or abort if  
the default demo image is missing. Currently only '.hdr' RGBE images are  
supported.  
  
See [SimpleHDRDemo](SimpleHDRDemo) for explanations. This is the same demos, but displaying  
stereoscopically on Linux + X11 via the special Linux hack enabled by the  
Linux only [PsychImaging](PsychImaging) task  
  
[PsychImaging](PsychImaging)('AddTask', 'General', 'UseStaticHDRHack', hdrMeta);  
  
See help [PsychImaging](PsychImaging) in the 'UseStaticHDRHack' section for explanations,  
background info and setup instructions.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/SimpleHDRLinuxStereoDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/SimpleHDRLinuxStereoDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/SimpleHDRLinuxStereoDemo.m</code>
</div>

