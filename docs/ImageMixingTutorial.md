# [ImageMixingTutorial](ImageMixingTutorial)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[PsychTutorials](PsychTutorials)

[ImageMixingTutorial](ImageMixingTutorial)([mode=1][, ms=200][, myimgfile])  
  
[ImageMixingTutorial](ImageMixingTutorial) shows how to use a combination of alpha blending,  
offscreen windows and some basic image processing shaders to mix two  
images together, using a "mix weight mask" (aka alpha mask) which itself  
is dynamically updated via [Screen](Screen)() drawing commands like [DrawTexture](DrawTexture),  
[DrawTexture](DrawTexture) with shaders, [FillRect](FillRect) etc. This allows for interesting  
new gaze contingent displays or dynamically changing binocular rivalry  
stimuli.  
  
### The basic working principle:  
  
1. An offscreen window is created which stores the alpha blend mask  
   with per-pixel mixing weights. ("masktex" in the code).  
  
2. The offscreen window stores the mix weights in its \*luminance\* channel,  
   (which is the same as the red channel for technical reasons). This way,  
   grayscale "luminance" values (luminance == red == green == blue) directly  
   encode "mixing weights". As we use a normalized 0-1 color range in this  
   demo ("[PsychDefaultSetup](PsychDefaultSetup)(2)"), a grayscale value from 0 - 1 (aka from  
   black to white) directly corresponds to a mix weight from 0 - 1. This  
   allows us to use standard [Screen](Screen)() 2D drawing commands as usual to draw  
   a mix weight mask as a grayscale image into the offscreen window without  
   any deeper knowledge or thought about alpha blending. We can use all  
   drawing commands to quickly and dynamically update or redraw the grayscale  
   image in the offscreen window to create a dynamically changing mix weight  
   mask.  
  
3. A shader is used to convert the grayscale image in the offscreen window  
   into a alpha mask and draw that alpha mask into the framebuffer of the  
   onscreen window, thereby setting the alpha channel of the onscreen window  
   to the desired mix weight mask for mixing the actual stimulus images.  
  
4. Alpha blending is used to draw the two target stimulus images, mixing  
   them together according to the alpha channel created in step 3 from the  
   grayscale weight mask dynamically created in step 2.  
  
5. The final mixed stimulus, e.g., a binocular rivalry stimulus, is shown  
   to the subject, rinse wash, repeat with step 2.  
  
This demo shows how to use normalized color ranges from 0 - 1 as a more  
natural representation of such alpha mix weights. It shows how to use the  
'WeightedColorComponentSum' shader to both morph up to 4 masks together into  
one weight mask, and as an alternate use, how to move the content of the  
red channel of a window (== luminance/grayscale channel in a grayscale image)  
into the alpha channel, allowing to implement step 3 above. It also uses  
alpha blending in combination with a separate offscreen window in a non-usual  
way to allow to logically separate the process of creating/updating a mix weight  
mask from the process of actually applying that mask to a pair of stimulus images.  
This approach is not neccessary for simple gaze-contingent displays or rivalry  
stimuli (cfe. [GazeContingentDemo](GazeContingentDemo) / [GazeContingentTutorial](GazeContingentTutorial) / [BubbleDemo](BubbleDemo) for simpler  
approaches). It is beneficial for stimuli which require complex mix masks, or  
complex dynamically updated mix masks, as it allows to implement an approach that  
reduces implementation complexity and is more natural or easier on the brain of  
the implementer of the stimulus, with less potential for coding errors or confusion  
about side effects of alpha blending.  
  
The tutorial allows you to switch between different stages of the processing  
involved in this approach and see their effects "live", by use of different  
keys on the keyboard, and to draw a dynamic mask via use of the mousecursor  
as a paint brush. It also shows some automatically running use of procedural  
shaders, texture animation and other [Screen](Screen) drawing primitives.  
  
This tutorial is powerful in its potential use cases, but requires significant  
customization for specific paradigms, and a good and careful reading of the code.  
  
For a much more simple demo and application of the technique, have a look at  
the [SimpleImageMixingDemo](SimpleImageMixingDemo).m, written and contributed by Natalia Zaretskaya.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/PsychTutorials/ImageMixingTutorial.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/PsychTutorials/ImageMixingTutorial.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/PsychTutorials/ImageMixingTutorial.m</code>
</div>

