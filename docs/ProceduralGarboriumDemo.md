# [ProceduralGarboriumDemo](ProceduralGarboriumDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[ProceduralGarboriumDemo](ProceduralGarboriumDemo)([ngabors=200]) -- An aquarium full of cute little procedural gabors!  
  
This demo shows how to use the [Screen](Screen)('DrawTextures') command to draw a  
large number of similar images quickly - in this case, Gabor patches of  
different position, size and orientation. It also shows how to achieve  
fast, mathematically correct, linear superposition of image patches by  
use of alpha blending and the Psychtoolbox imaging pipeline. While you  
could always achieve proper superposition by precomputing large images in  
Matlab, then drawing them as textures, the use of alpha blending allows  
to offload the computations to your graphics hardware - this allows  
speedups by factors of more than 100x in some cases!  
  
Furthermore the demo demonstrates how to use procedural shading to  
compute gabor patches on-the-fly instead of precomputing a prototypical  
gabor patch image within Matlab. The command [CreateProceduralGabor](CreateProceduralGabor)()  
allows to generate such a procedural gabor and then draw it with the  
normal 'DrawTexture' or 'DrawTextures' texture drawing commands. However,  
this gabor patch is not a image like a normal texture. Instead it is  
computed during each draw operation by a so called GLSL shader program --  
the gabor formula is evaluated on the fly inside your fast graphics card.  
  
This method has a few advantages over the standard texture based method  
(as demonstrated in [GarboriumDemo)](GarboriumDemo)):  
  
- GPU's are extremely fast at this kind of jobs, so the method is  
significantly faster on modern GPU's, especially for large patches,  
allowing for even higher redraw rates.  
  
- As the formula is evaluated on the fly for each output pixel, there are  
no resampling artifacts, regardless of size of your gabor.  
  
- You can change all interesting stimulus parameters on the fly -- change  
contrast, aspect ratio, spatial constant, frequency, phase, orientation  
etc. for each patch during each redraw cycle without the need to  
recompute any matrices and without any speed penalty.  
  
The downsides of this method are the need for recent graphics hardware  
(GPU's) and the fact that the stimulus definition formula needs to be  
implemented as a shader program in the GLSL language, which is less easy  
to use - and less forgiving of programming errors - than the simple and  
easy Matlab language. This means that you're either restricted to our  
predifined set of primitives, or you'll have some steep learning curve.  
Currently PTB provides several such stimuli (see the [CreateProcedural](CreateProcedural)\*  
series of functions for details).  
  
The demo shows "an aquarium" of many cute little gabor patches, each moving  
into a random direction. Sometimes the gabors intersect, in that case  
you'll see a linear superposition of them. The gabors also shift phase  
and pulse (aspect ratio modulation) to make them more life-like -- and to  
demonstrate runtime change of interesting stimulus parameters, of course.  
  
Each frame of the animation contains 'ngabors' patches, ngabors defaults  
to 200. Change the number as first optional parameter 'ngabors' if you want  
to exercise your graphics hardware and cpu.  
  
You can exit the demo by pressing any key on the keyboard.  
  
This demo needs recent graphics hardware with floating point framebuffer  
support: ATI Radeon X1000 and later, [NVidia](NVidia) [GeForce](GeForce) 6000 and later.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/ProceduralGarboriumDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/ProceduralGarboriumDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/ProceduralGarboriumDemo.m</code>
</div>

