# [Datapixx('SetPropixxDlpSequenceProgram')](Datapixx-SetPropixxDlpSequenceProgram) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetPropixxDlpSequenceProgram' [, program=0]);

Set [PROPixx](PROPixx) DLP sequencer.  
The [PROPixx](PROPixx) uses an LED light engine to illuminate a DLP imaging chip. The  
specified "program" determines how video bit planes drive the [LEDs](LEDs) and DLP  
micromirrors. program can take on one of the following values:  
   0: RGB, Normal video processing.  
   1: RB3D, Red/Blue channels contain left/right-eye stereoscopic greyscale  
images  
.       This mode only supports refresh rate 120 Hz or less.  
   2: QUAD4X, 4 display quadrants are projected at 4x refresh rate, up to 480Hz  
      Frame order is: [TopLeft](TopLeft), [TopRight](TopRight), [BottomLeft](BottomLeft), [BottomRight](BottomRight).  
   5: QUAD12X, 4 display quadrants x3 RGB channels are projected greyscale at  
12x refresh rate, up to 1440Hz  
      Frame order is: [RedTopLeft](RedTopLeft), [RedTopRight](RedTopRight), [RedBottomLeft](RedBottomLeft), [RedBottomRight](RedBottomRight),  
[GreenTopLeft](GreenTopLeft)...[BlueBottomRight](BlueBottomRight).  
   6: RGB, Calibrated high bit depth.  
   9: GREY3X, Converts 640x1080@360Hz RGB video to 1920x1080@720Hz greyscale  
video by using each color information  
      as one pixel at 360Hz and adding a blank frame between to create the  
720Hz.  
   10:GREY720, Uses 1280x720@240Hz RGB to show sequentially the red, green and  
blue frames in greyscale at 720Hz.  
  


###See also:

