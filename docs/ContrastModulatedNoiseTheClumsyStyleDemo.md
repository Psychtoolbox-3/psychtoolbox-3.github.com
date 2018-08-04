# [ContrastModulatedNoiseTheClumsyStyleDemo](ContrastModulatedNoiseTheClumsyStyleDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[ContrastModulatedNoiseTheClumsyStyleDemo](ContrastModulatedNoiseTheClumsyStyleDemo)([noisesize=512] [, staticnoise=0])  
  
This demo shows how to render contrast modulated noise with old, outdated  
graphics hardware. A rectangular image with random noise of size  
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
alpha-channel encodes contrast values between 0.0 and 1.0 in steps of  
1/256th. Then we draw a noise texture of fixed contrast into the  
framebuffer and the alpha-blending hardware takes care of modulating the  
contrast of the drawn noise texture with the values from the  
alpha-channel.  
  
Hardware requirements: ATI Radeon 8500 or later, [NVidia](NVidia) Geforce2 or later  
on [MacOS](MacOS)/X. Not Intel-GMA 950 of Intel [MacBook](MacBook)!  
  
Limitations: This demo is meant to run on outdated graphics hardware, so  
it can't make use of the Psychtoolbox imaging pipeline, which would allow  
for a very elegant, flexible and fast implementation. We use a multi-pass  
approach here to work around hardware restrictions as much as possible.  
Some of the limitations of this approach: Contrast modulation is  
restricted to 0.0 - 1.0 and accuracy is limited to 256 levels. Clamping  
of your noise matrix (has to fit in the "normal" 8 bit 256 gray level  
range) can change the noise distribution in unwanted ways. The multi-pass  
approach used here is pretty inefficient, so redraw rates are pretty low,  
e.g., max. 15 fps on a fast [MacBookPro](MacBookPro) with ATI Radeon X1600.  
  
If you have recent graphics hardware (ATI Radeon X1000 or later, [NVidia](NVidia)  
Geforce 6000 and later), take a look at [ContrastModulatedNoiseTheElegantStyleDemo](ContrastModulatedNoiseTheElegantStyleDemo).m  
instead. That demo takes advantage of the imaging pipeline, greatly  
simplifying stimulus programming and lifting basically all restrictions  
of the approach presented here. Achievable redraw rates are also much  
higher that way!  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/ContrastModulatedNoiseTheClumsyStyleDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/ContrastModulatedNoiseTheClumsyStyleDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/ContrastModulatedNoiseTheClumsyStyleDemo.m</code>
</div>

