# [FDFDemo](FDFDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[OpenGL4MatlabDemos](OpenGL4MatlabDemos)

[FDFDemo](FDFDemo)(dotDensity, dotLifetime) - Demo of "formless dot field" stimulus  
via moglFDF.  
  
This demo generates a simple "formless dot field" random dot motion  
stimulus to create "structure from motion" percept by use of the moglFDF  
function for formless dot field rendering. See "help moglFDF" for more  
details.  
  
The demo shows a simple spinning 3D sphere, rendered as random dot  
stimulus.  
  
### The following optional parameters can be provided to [FDFDemo](FDFDemo):  
  
dotDensity = Number of dots to use for both, the background- and  
             foreground distribution. Defaults to 10000.  
  
dotLifetime = Lifetime of dots in frames. Defaults to 10 frames.  
  
  
### Control keys:  
  
[ESCape](ESCape) key finishes the demo.  
  
SPACE key toggles between a slowly rotating sphere and a static sphere.  
  
'd' toggles the display between the formless dot field stimulus and some  
debug visualization.  
  
't' toggles drawing of foreground dots in the colors defined by the  
texture map of the drawn object.  
  
'r' resets the distribution to empty, then incrementally recreates it.  
  
'h' resets the distribution to a completely new random one.  
  
Arrow left/right control the density of dots, the 'dotDensity' paramter  
in decrements/increments of 5%.  
  
Arrow up-/down controls the 'dotLifetime' in steps of +/- 1.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/FDFDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/FDFDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/FDFDemo.m</code>
</div>

