# [Datapixx('SetDoutValues')](Datapixx-SetDoutValues) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetDoutValues', bitValues [, bitMask = 0x00FFFFFF]);

For each of the 24 bits set in "bitMask", set the digital output to the value in  
the corresponding "bitValues". bitMask defaults to all bits enabled, so  
bitValues overwrites all the digital outputs.  
See [DatapixxDout](DatapixxDout)\*Demo files for examples.  
  


###See also:
[GetDoutValues](Datapixx-GetDoutValues), [SetDoutSchedule](Datapixx-SetDoutSchedule), [EnableDoutDinLoopback](Datapixx-EnableDoutDinLoopback)
