# [ContrastModulatedNoiseTheElegantStyleDemo](ContrastModulatedNoiseTheElegantStyleDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[ContrastModulatedNoiseTheElegantStyleDemo](ContrastModulatedNoiseTheElegantStyleDemo)([noisesize=512] [, staticnoise=0])  
  
This demo shows how to render contrast modulated noise efficiently on  
current state of the art graphics hardware by use of the Psychtoolbox  
imaging pipeline and high precision framebuffers.  
  
A rectangular image with random noise of size  
'noisesize' by 'noisesize' pixels is created, then drawn to the display.  
  
We use alpha-blending tricks to modulate the contrast of the noise in  
realtime. In this demo you can move the mouse pointer to drag around a  
"modulation disk" of 50 pixels diameter. Noise inside the disk has a  
different contrast 'fgcontrast' from the rest of the image, which has a  
contrast of 'bgcontrast' (see top of code for fgcontrast and bgcontrast).  
  
You can press the cursor left and cursor right keys to decrement or  
increment the contrast inside the disk in steps of 0.01 units. Press  
cursor up key to set the inside disk contrast equal to outside disk  
contrast. Press ESCAPE key to finish the demo.  
  
The optional 'staticnoise' flag - if set to 1 - will render a static  
noise image instead of one that changes at each frame. That's faster  
because one doesn't need to recreate the noise texture each frame.  
  
How this works? Basically we use standard [Screen](Screen) 2D drawing commands to  
draw a "contrast values weight map" into the alpha-channel, so the  
alpha-channel encodes contrast values between 0.0 and 1.0.  
Then we draw a noise texture of fixed contrast into the framebuffer  
and the alpha-blending hardware takes care of modulating the  
contrast of the drawn noise texture with the values from the  
alpha-channel.  
  
Hardware requirements: ATI Radeon X-1000 or later, [NVidia](NVidia) Geforce 6000 or  
later. Recommended is Radeon HD2000/3000/... or Geforce-8000/9000/...  
hardware for maximum fun!  
  
The allowable contrast values for standard 2D drawing commands are  
limited to the range 0.0 to 1.0 on [MacOS](MacOS)/X, they are not limited on  
MS-Windows or GNU/Linux. Precision is set to 16bpc float, ie. about 3  
digits behind the decimal point or 1024 discriminable levels. On the most  
recent ATI HD-2000 and [NVidia](NVidia) Geforce 8000 hardware one can lift this limit  
to 32bpc float -- 6.5 digits or about 8 million discriminable levels by a  
one-line code change in this script ;-)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/ContrastModulatedNoiseTheElegantStyleDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/ContrastModulatedNoiseTheElegantStyleDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/ContrastModulatedNoiseTheElegantStyleDemo.m</code>
</div>

