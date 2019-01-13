# [Datapixx('SetPropixxDlpSequenceProgram')](Datapixx-SetPropixxDlpSequenceProgram) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetPropixxDlpSequenceProgram' [, program=0]);

Set [PROPixx](PROPixx) DLP sequencer.  
The [PROPixx](PROPixx) uses an LED light engine to illuminate a DLP imaging chip. The  
specified "program" determines how video bit planes drive the [LEDs](LEDs) and DLP  
micromirrors. program can take on one of the following values:  
   0: RGB, Normal video processing.  
   1: RB3D, Red/Blue channels contain left/right-eye stereoscopic grayscale  
images  
   2: QUAD4X, 4 display quadrants are projected at 4x refresh rate, up to 480Hz  
      Frame order is: [TopLeft](TopLeft), [TopRight](TopRight), [BottomLeft](BottomLeft), [BottomRight](BottomRight).  
   5: QUAD12X, 4 display quadrants x3 RGB channels are projected grayscale at  
12x refresh rate, up to 1440Hz  
      Frame order is: [RedTopLeft](RedTopLeft), [RedTopRight](RedTopRight), [RedBottomLeft](RedBottomLeft), [RedBottomRight](RedBottomRight),  
[GreenTopLeft](GreenTopLeft)...[BlueBottomRight](BlueBottomRight).  
  


###See also:

