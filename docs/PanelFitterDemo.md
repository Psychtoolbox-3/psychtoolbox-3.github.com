# [PanelFitterDemo](PanelFitterDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[PanelFitterDemo](PanelFitterDemo) - Demonstrate use of the panel fitter.  
  
This demo shows how to use [Screen](Screen)()'s panel fitter function by using the  
high-level setup code in [PsychImaging](PsychImaging)().  
  
The panelfitter allows to implement "rotated framebuffers", which have a  
shape (width and height in pixels) that corresponds to a display device  
that is rotated by increments of 90 degrees with respect to its "natural"  
upright orientation (typically landscape). E.g., assume you have a flat  
panel with a natural landscape orientation - more wide than high - and a  
resolution of 1920 x 1080 pixels. Now for some reason you want to turn  
your panel into "portrait" orientation - more high than wide - by  
rotating it by 90 degrees. Drawing stimulus images for such a rotated  
display would be inconvenient, as everything would be shown tilted by 90  
degrees to your subject. Here the panelfitter can help by providing a  
framebuffer that is rotated by 90 degrees wrt. its normal shape, ie., the  
framebuffer is 1080 x 1920 pixels in size instead of its natural 1920 x  
1080 pixels. Drawing into such a framebuffer becomes natural and easy  
again, as the shape and orientation of the framebuffer corresponds to the  
effective shape and orientation of your display device.  
  
Such rotations can be requested from the panelfitter by the  
[PsychImaging](PsychImaging)('AddTask', 'General', 'UseDisplayRotation', angle); command.  
  
Why not simply use the "Rotate display" buttons or settings in the  
display control GUI of your operating system? Because the method by which  
operating systems and graphics cards do implement that display rotation  
will usually severely interfere with visual stimulus onset timing and/or  
stimulus onset timestamping -- you lose control over your stimulus  
presentation timing. Our panelfitter makes sure timing stays under  
control.  
  
Another application of the panelfitter is if you want to operate your  
flat panel or video projector at a different resolution or image size  
than its native resolution. Good old CRT monitors didn't have a native  
resolution, they were happy to display at a wide range of different  
resolutions and refresh rates. Modern flat panels and projectors do have  
only one true native resolution, which is their maximum resolution, due  
to their fixed pixel grid. If you want to set such a display to a  
different resolution, your graphics hardware or display device will use  
digital image processing to scale and resize the input video signal from  
its set resolution to the native resolution of the device. This  
introduces lag due to processing delays, and possibly non-deterministic  
timing variance in visual stimulus onset, therefore you should avoid such  
non-native resolutions and run your displays at native (maximum)  
resolution. If you still want to display stimulus images at a different  
size than the panels native resolution, the panelfitter can help you. It  
provides you with a framebuffer of selectable size and then performs the  
scaling and resizing of the stimulus image in that framebuffer to the  
true size of the panels framebuffer resolution. In other words, it fits  
the content onto the panel, hence the name "panelfitter". You can use the  
[PsychImaging](PsychImaging)('AddTask', 'General', 'UsePanelFitter', fitSize, 'Centered');  
command to define the size of your framebuffer ('fitSize') and the  
strategy for placing and scaling the image onto the panel.  
  
Again, operating systems allow you to select different resolutions and  
fitting modes in their display GUI controls, but the methods by which  
non-native resolutions and fittings are implemented by current operating  
systems and graphics cards can severely interfere with stimulus onset  
timing and timestamping, or with low level stimulus properties, due to  
the digital filtering, resampling and blurring involved. Our panelfitter  
prevents timing artifacts and gives you more control over other  
properties.  
  
### Please note that use of our panelfitter is also not totally free:  
  
a) Currently display rotation and image scaling don't go well together.  
   One or the other works well, but both combined can exhibit bugs and  
   artifacts. These are limitations of our current high-level setup code.  
   You could probably use the [Screen](Screen)('PanelFitter') low-level setup  
   command directly to get a well working solution for your specific  
   needs, should you require scaling and rotation at the same time. Or  
   you could fix and extend our high-level setup code in [PsychImaging](PsychImaging).m.  
  
b) Multisample anti-aliasing does not work together with display rotation  
   on older graphics hardware, or with Apple OSX versions up to and  
   including 10.9 "Mavericks". It will work on modern GPU's under Linux  
   or Windows if they at least support [OpenGL](OpenGL) 3.2, but not on the same  
   GPU's under OSX, as this is a purely political restriction introduced  
   by Apple, making OSX less useful than it could be.  
  
c) There is a small performance impact on the order of < 1 millisecond  
   per [Screen](Screen)('[Flip](Flip)') with modern graphics cards due to the processing  
   involved.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/PanelFitterDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/PanelFitterDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/PanelFitterDemo.m</code>
</div>

