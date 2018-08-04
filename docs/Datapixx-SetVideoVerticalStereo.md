# [Datapixx('SetVideoVerticalStereo')](Datapixx-SetVideoVerticalStereo) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Configure doubling refresh rate to generate left/right eye images on successive  
frames.  
The Datapixx has an industry standard VESA mini-DIN-3 connector for driving  
stereo goggles. The easiest way to drive the goggles is to have the Datapixx  
receive a single video frame containing the left-eye image on top, and the  
right-eye image on the bottom. The Datapixx can then insert a vertical sync  
between the left and right images, causing the two eyes to be displayed  
sequencially on the display, at twice the original refresh rate. When in this  
mode, the Datapixx will automatically drive the VESA stereo port to align  
perfectly with the stereoscopic image.  
The [SetVideoVerticalStereo](SetVideoVerticalStereo) "mode" can take on one of the following values:  
   0: NO\_STEREO, normal operation  
   1: STEREO, Datapixx doubles refresh rate, shows L/R images, drives goggles  
   2: AUTO (default value), Datapixx automatically switches to STEREO when the  
video's vertical resolution exceeds it's horizontal resolution.  
When using vertical stereo mode, it can be useful to specify tall frame buffers  
in order to maintain constant pixel spacing. One example which works well is to  
specify a frame buffer of 800x1243 pixels at 60 Hz. The Datapixx inserts a  
vertical sync/blank in the middle 43 lines of the image, resulting in an 800x600  
image for each of the left and right eyes at 120 Hz. The utilities used to  
generate unusual DVI resolutions (like 800x1243) depend on the host operating  
system.  For example:  
   -OS X users could download [SwitchResX](SwitchResX) at http://www.madrau.com/indexSRX4.html  
   -Windows could use [PowerStrip](PowerStrip) from http://www.entechtaiwan.com/util/ps.shtm  
   -Linux users are often able to write their own video driver "mode lines"  
  


###See also:
[SetVideoMode](Datapixx-SetVideoMode), [GetVideoStatus](Datapixx-GetVideoStatus)
