# [PsychPortAudio('UseSchedule')](PsychPortAudio-UseSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction

PsychPortAudio('UseSchedule', pahandle, enableSchedule [, maxSize = 128]);

Enable or disable use of a preprogrammed schedule for audio playback on audio  
device 'pahandle'.  
Schedules are similar to playlists on your favorite audio player. A schedule  
allows to define a sequence of distinct sounds to play in succession. When  
[PsychPortAudio](PsychPortAudio)('Start') is called, processing of the schedule begins and the  
first programmed sound snippet is played, followed by the 2nd, 3rd, ... until  
the whole schedule has been played once and playback stops. You can add new  
sound snippets to the schedule while playback is running for uninterrupted  
playback of long sequences of sound.  
Each sound snippet or slot in the schedule defines a soundbuffer to play back  
via a 'bufferhandle', within the buffer a subsegment (a so called playloop)  
defined by start- and endpoint, and a number of repetitions for that playloop.  
This subfunction allows to either enable use of schedules by setting the  
'enableSchedule' flag to 1, in which case a schedule with a maximum of 'maxSize'  
distinct slots is created ('maxSize' defaults to 128 slots), or to disable use  
of schedules by setting 'enableSchedule' to 0, in which case [PsychPortAudio](PsychPortAudio)  
reverts back to its normal playback behaviour and an existing schedule is  
deleted.  
A 'enableSchedule' setting of 2 will reset an existing schedule, ie. clear it of  
all its entries, so it is ready to be rewritten with new entries. You should  
reset and rewrite a schedule each time after playback/processing of a schedule  
has finished or has been stopped.  
A 'enableSchedule' setting of 3 will reactivate an existing schedule, ie.  
prepare it for a replay.  
See the subfunction 'AddToSchedule' on how to populate the schedule with actual  
entries.  
  


###See also:
[FillBuffer](PsychPortAudio-FillBuffer) Start Stop [RescheduleStart](PsychPortAudio-RescheduleStart) [AddToSchedule](PsychPortAudio-AddToSchedule)
