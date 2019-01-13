# [Datapixx('EnableVideoStereoBlueline')](Datapixx-EnableVideoStereoBlueline) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('EnableVideoStereoBlueline');

Enables the bottom raster line to be interpreted as a VESA 3D left/right eye  
code.  
If the left 1/4 of the line is blue or white, and the remainder of the line is  
black, then the frame will be interpreted as containing left-eye data. If the  
left 3/4 of the line is blue or white, and the remainder of the line is black,  
then the frame will be interpreted as containing right-eye data.  
See [ImagingStereoDemo](ImagingStereoDemo).m for an example.  Invoke using [ImagingStereoDemo](ImagingStereoDemo)(1,1).  
  


###See also:
[DisableVideoStereoBlueline](Datapixx-DisableVideoStereoBlueline), [SetVideoStereoVesaWaveform](Datapixx-SetVideoStereoVesaWaveform)
