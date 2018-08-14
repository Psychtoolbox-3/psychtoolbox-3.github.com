# [Datapixx('EnableDoutButtonSchedules')](Datapixx-EnableDoutButtonSchedules) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Normally digital output schedules are initiated via calls to [StartDoutSchedule](StartDoutSchedule).  
[EnableDoutButtonSchedules](EnableDoutButtonSchedules) causes the [DATAPixx](DATAPixx) to automatically initiate a  
digital output schedule whenever a falling edge on one of the digital inputs has  
been detected. Transitions on the 16 different button inputs (DIN0-DIN15) will  
initiate 16 different schedules. Transitions on DIN0 will use the schedule  
buffer specified in the call to [SetDoutSchedule](SetDoutSchedule). Transitions on DIN1-DIN15 will  
automatically use higher address buffers at 4kB increments.  
  


###See also:
[DisableDoutButtonSchedules](Datapixx-DisableDoutButtonSchedules), [GetDoutStatus](Datapixx-GetDoutStatus)
