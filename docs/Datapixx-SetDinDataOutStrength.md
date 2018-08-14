# [Datapixx('SetDinDataOutStrength')](Datapixx-SetDinDataOutStrength) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Although DIN is primarily intended to be a digital \_input\_ system, it is  
possible to turn around these I/Os, to drive outputs at up to 3.3V.  
[SetDinDataOutStrength](SetDinDataOutStrength) offers coarse control over the output drive strength. One  
application is controlling the intensity of illumunated response buttons.  
-"strength" should be within the range 0-1. The actual implementation varies  
drive strength from minimum to maximum in increments of 1/16 of full strength.  
See [DatapixxDin](DatapixxDin)\*Demo files for examples.  
  


###See also:
[SetDinDataDirection](Datapixx-SetDinDataDirection), [SetDinDataOut](Datapixx-SetDinDataOut), [GetDinStatus](Datapixx-GetDinStatus)
