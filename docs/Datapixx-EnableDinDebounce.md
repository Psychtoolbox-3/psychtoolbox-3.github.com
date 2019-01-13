# [Datapixx('EnableDinDebounce')](Datapixx-EnableDinDebounce) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('EnableDinDebounce');

Enable a 30 millisecond debounce interval on the digital inputs. The first DIN  
transition is logged immediately, however successive transitions are ignored for  
the next 30 ms. This can be used to remove contact bounce noise from button  
boxes.  
See [DatapixxDin](DatapixxDin)\*Demo files for examples.  
  


###See also:
[DisableDinDebounce](Datapixx-DisableDinDebounce), [GetDinStatus](Datapixx-GetDinStatus)
