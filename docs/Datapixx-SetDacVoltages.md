# [Datapixx('SetDacVoltages')](Datapixx-SetDacVoltages) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetDacVoltages', channelVoltagePairs);

Set the voltages for a list of DAC channels. -"channelVoltagePairs" is a list of  
DAC channels and their associated voltages; eg: Datapixx('SetDacVoltages', [0  
2.5 3 -2.5]) would set DAC channel 0 to +2.5V and DAC channel 3 to -2.5V. A 2D  
array can also be passed; eg: Datapixx('SetDacVoltages', [0:3 ; 5 4 3 2]) would  
set ch0 to 5V, ch1 to 4V, ch2 to 3V, ch3 to 2V.  
See [DatapixxDac](DatapixxDac)\*Demo files for examples.  
  


###See also:
[GetDacVoltages](Datapixx-GetDacVoltages), [SetDacSchedule](Datapixx-SetDacSchedule), [EnableDacAdcLoopback](Datapixx-EnableDacAdcLoopback)
