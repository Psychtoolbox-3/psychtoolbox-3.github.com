# [Datapixx('EnableDacAdcLoopback')](Datapixx-EnableDacAdcLoopback) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Enable an internal loopback from the DAC outputs to the ADC inputs. This causes  
voltages programmed into the DAC output channels to appear on the ADC input  
channels. This convenient feature can be useful when developing analog  
acquisition and analysis routines. Your routines can be tested using simulated  
analog waveforms which play on the DAC scheduler.  
Because there are more ADC channels than DAC channels in the system, the  
following loopback mapping used:  
   -DAC0 drives ADC0/2/4/6/8/10/12/14  
   -DAC1 drives ADC1/3/5/7/9/11/13/15  
   -DAC2 drives REF0  
   -DAC3 drives REF1  
See [DatapixxAdc](DatapixxAdc)\*Demo files for examples.  
  


###See also:
[DisableDacAdcLoopback](Datapixx-DisableDacAdcLoopback), [GetAdcStatus](Datapixx-GetAdcStatus)
