# [Datapixx('DisableAdcFreeRunning')](Datapixx-DisableAdcFreeRunning) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('DisableAdcFreeRunning');

Disable free-running mode for the analog-to-digital converters. In free-running  
mode, the hardware ADC components convert continuously at the system's maximum  
possible rate of 200 kHz. When not in free-running mode, the hardware components  
only initiate conversions at the precise moment that an ADC schedule requires a  
new datum. Recommended usage is to only enable free-running mode when manually  
calling [GetAdcVoltages](GetAdcVoltages) to monitor analog inputs at low rates. When running a  
high-speed analog acquisition schedule, it is preferable to disable the  
free-running mode, thus eliminating the 5 microsecond uncertainty in the  
sampling aperture.  
See [DatapixxAdc](DatapixxAdc)\*Demo files for examples.  
  


###See also:
[EnableFreeRunning](Datapixx-EnableFreeRunning), [GetAdcStatus](Datapixx-GetAdcStatus)
