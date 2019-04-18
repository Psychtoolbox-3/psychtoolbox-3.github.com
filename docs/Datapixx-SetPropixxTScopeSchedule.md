# [Datapixx('SetPropixxTScopeSchedule')](Datapixx-SetPropixxTScopeSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetPropixxTScopeSchedule', scheduleOnset, scheduleRate, maxScheduleFrames [, startPage=1] [, nPages=maxScheduleFrames]);

Configure a schedule for T-Scope image sequence playback on [PROPixx](PROPixx).  
-"scheduleOnset" is the desired delay (in double precision seconds) between  
schedule initiation, and when the T-Scope's second page replaces the cover page.  
-"scheduleRate" is the rate at which successive T-Scope pages are presented.  
scheduleRate has two formats.  It can be a single number, or a 2 element array.  
If it is a single number, then it specifies integer pages/second. If it is a 2  
element array, then the first element specifies the rate, and the second element  
specifies the units of the rate.  
If units = 1, then the rate is interpreted as integer pages/second.  
If units = 2, then the rate is interpreted as integer pages/video frame being  
received on DVI input.  
If units = 3, then the rate is interpreted as double precision seconds/page  
(frame period).  
Regardless of the actual format chosen, the resulting frame rate cannot exceed  
10 kHz.  
-"maxScheduleFrames" has two modes, depending on whether the T-Scope animation  
duration is known. If the duration is known (eg: 1000 frames), then just pass  
1000 to maxScheduleFrames. In this mode, once the T-Scope schedule is started  
with [StartPropixxTScopeSchedule](StartPropixxTScopeSchedule), the schedule will terminate automatically when  
maxScheduleFrames has been reached. If the duration is not known in advance,  
then pass 0 to maxScheduleFrames. In this mode, the playback will continue until  
the schedule is manually stopped using [StopPropixxTScopeSchedule](StopPropixxTScopeSchedule).  
-"startPage" specifies the start of the [PROPixx](PROPixx) RAM buffer which holds the image  
data. This first page is called the "cover page", and is first shown when  
[EnablePropixxTScopePrepRequest](EnablePropixxTScopePrepRequest) is called. Use [WritePropixxTScopePages](WritePropixxTScopePages) to  
download the images to this address before calling [StartPropixxTScopeSchedule](StartPropixxTScopeSchedule).  
-"nPages" specifies the number of image frames in the [PROPixx](PROPixx) RAM which should  
be used in this sequence. If the schedule requests more pages than nPages, then  
it will automatically wrap back to the page following the cover page. This will  
result in a periodic stimulus. For many applications, the complete stimulus is  
represented by a single pass through a fixed block of pages. In these cases,  
nPages could be left at its default value of maxScheduleFrames. Note that every  
call to [StartPropixxTScopeSchedule](StartPropixxTScopeSchedule) must be preceeded by a call to  
[SetPropixxTScopeSchedule](SetPropixxTScopeSchedule) (ie: multiple calls to [StartPropixxTScopeSchedule](StartPropixxTScopeSchedule) each  
require their own call to [SetPropixxTScopeSchedule)](SetPropixxTScopeSchedule)).  
Note that schedule timing is implemented in hardware with microsecond precision.  
See [Propixx10kHzTScopeDemo](Propixx10kHzTScopeDemo).m for an example.  
  


###See also:
[EnablePropixxTScope](Datapixx-EnablePropixxTScope), [EnablePropixxTScopePrepRequest](Datapixx-EnablePropixxTScopePrepRequest), [WritePropixxTScopePages](Datapixx-WritePropixxTScopePages), [StartPropixxTScopeSchedule](Datapixx-StartPropixxTScopeSchedule)
