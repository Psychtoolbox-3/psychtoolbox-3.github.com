# [BitsPlusMovieDemo](BitsPlusMovieDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BitsPlusToolbox](BitsPlusToolbox)>[BitsPlusDemos](BitsPlusDemos)

[BitsPlusMovieDemo](BitsPlusMovieDemo)  
  
[BitsPlusMovieDemo](BitsPlusMovieDemo) displays a counterphase flickering grating, by lookup  
table animation, using the Bits++ box.  
  
Note that you need to precompute the cluts and write them into  
offscreen memory in advance, so that the blits happen fast.  In  
this example, each clut goes into its own offscreen window.  In  
real applications, we have found that the precomputation is considerably  
faster if we allocate one large offscreen window and put each clut  
into a different rect inside of it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusDemos/BitsPlusMovieDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusDemos/BitsPlusMovieDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusDemos/BitsPlusMovieDemo.m</code>
</div>

