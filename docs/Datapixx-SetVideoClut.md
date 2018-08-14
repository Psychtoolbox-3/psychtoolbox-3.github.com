# [Datapixx('SetVideoClut')](Datapixx-SetVideoClut) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Send a 256 row \* 3 column color lookup table to the Datapixx.  
The three columns contain the red, green, and blue components respectively. The  
data are in the range 0-1, and map to the Datapixx 16-bit video DAC values, with  
0 mapping to a DAC value of 0, and 1 mapping to a DAC value of 65535. The color  
lookup table is used by the Datapixx when in video mode LUT\_48, and for the  
overlay when in video mode MONO\_16. The CLUT is sent to the Datapixx over USB,  
and is copied to the hardware [CLUTs](CLUTs) during the next vertical blanking interval.  
  


###See also:
[SetVideoMode](Datapixx-SetVideoMode), [RegWrRdVideoSync](Datapixx-RegWrRdVideoSync)
