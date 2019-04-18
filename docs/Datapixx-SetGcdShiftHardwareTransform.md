# [Datapixx('SetGcdShiftHardwareTransform')](Datapixx-SetGcdShiftHardwareTransform) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetGcdShiftHardwareTransform', xGain, xOffset, yGain, yOffset);

Specifies the transformation between hardware inputs and pixel shifts for gaze  
contingent displays.  
[PROPixx](PROPixx) Controller implements a gain and an offset when mapping hardware inputs  
to x/y pixel shifts. The Gain terms indicate how many pixels should be shifted  
for a full-scale hardware input, divided by 4. For example, the default value of  
512 means that a full-scale input from the ADC (+10V) will shift the image 2048  
pixels to the right. The Offset terms are in straight pixels. For example,  
assigning a value of 10 would cause the above +10V ADC to shift the image by  
2058 instead of 1048 pixels. Note that these gains and offsets are implemented  
as signed 16-bit values.  
  


###See also:
[EnablePropixxGcdShift](Datapixx-EnablePropixxGcdShift), [EnablePropixxGcdShiftHardware](Datapixx-EnablePropixxGcdShiftHardware), [EnableGcdShiftHardwareBridge](Datapixx-EnableGcdShiftHardwareBridge), [SetGcdShiftHardwareMode](Datapixx-SetGcdShiftHardwareMode)
