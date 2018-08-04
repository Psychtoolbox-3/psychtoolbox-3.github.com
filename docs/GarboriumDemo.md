# [GarboriumDemo](GarboriumDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[GarboriumDemo](GarboriumDemo)([ngabors=200] [, internalRotation=0]) -- An aquarium full of cute little gabors!  
  
This demo shows how to use the [Screen](Screen)('DrawTextures') command to draw a  
large number of similar images quickly - in this case, Gabor patches of  
different position, size and orientation. It also shows how to achieve  
fast, mathematically correct, linear superposition of image patches by  
use of alpha blending and the Psychtoolbox imaging pipeline. While you  
could always achieve proper superposition by precomputing large images in  
Matlab, then drawing them as textures, the use of alpha blending allows  
to offload the computations to your graphics hardware - this allows  
speedups by factors of more than 100x in some cases!  
  
The demo shows "an aquarium" of many cute little gabor patches, each moving  
into a random direction. Sometimes the gabors intersect, in that case  
you'll see a linear superposition of them.  
  
Each frame of the animation contains 'ngabors' patches, ngabors defaults  
to 200. Change the number as first optional parameter 'ngabors' if you want  
to exercise your graphics hardware and cpu.  
  
Normally the gabor paches rotate as a whole, a different method of  
rotation is so called internal texture rotation (see comments in code),  
which can be selected by setting the optional 2nd argument  
'internalRotation' to a value of 1.  
  
You can exit the demo by pressing any key on the keyboard.  
  
This demo needs recent graphics hardware with floating point framebuffer  
support: ATI Radeon X1000 and later, [NVidia](NVidia) [GeForce](GeForce) 6000 and later.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/GarboriumDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/GarboriumDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/GarboriumDemo.m</code>
</div>

