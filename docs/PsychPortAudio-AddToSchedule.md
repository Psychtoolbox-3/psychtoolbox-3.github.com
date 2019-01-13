# [PsychPortAudio('AddToSchedule')](PsychPortAudio-AddToSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction

[success, freeslots] = PsychPortAudio('AddToSchedule', pahandle [, bufferHandle=0][, repetitions=1][, startSample=0][, endSample=max][, UnitIsSeconds=0][, specialFlags=0]);

Add a new item to an existing schedule for audio playback on audio device  
'pahandle'.  
The schedule must have been created and enabled already via a previous call to  
'UseSchedule'. The function returns if the addition of a new item was  
successfull via the return argument 'success' (1=Success, 0=Failed), and the  
number of remaining free slots in 'freeslots'. Failure to add an item can happen  
if the schedule is full. If playback is running, you can simply retry after some  
time, because eventually the playback will consume and thereby free at least one  
slot in the schedule. If playback is stopped and you get this failure, you  
should reallocate the schedule with a bigger size via a proper call to  
'UseSchedule'.  
Please note that after playback/processing of a schedule has finished by itself,  
or due to 'Stop'ping the playback via the stop function, you should clear or  
reactivate the schedule and rewrite it, otherwise results at next call to  
'Start' may be undefined. You can clear/reactivate a schedule efficiently  
without resizing it by calling 'UseSchedule' with an enableFlag of 2 or 3.  
  
The following optional paramters can be used to define the new slot in the  
schedule:  
'bufferHandle' Handle of the audio buffer which should be used for playback of  
this slot. The default value zero will play back the standard audio buffer  
created by a call to 'FillBuffer'.  
'repetitions' How often should playback of this slot be repeated. Fractional  
positive values are allowed, the value zero (ie. infinite repetition) is not  
allowed in this driver release.  
'startSample' and 'endSample' define a playback loop - a subsegment of the audio  
buffer to which playback should be restricted, and 'UnitIsSeconds' tells if the  
given loop boundaries are expressed in audio sample frames, or in seconds  
realtime. See the help for the 'SetLoop' function for more explanation.  
  
'specialFlags' is an optional parameter to pass in some special mode flags to  
alter processing of a slot: Defaults to zero. If the value '1' is used (or  
added), then a slot is not automatically disabled after it has been used up, but  
it will be reused on repeated execution of the schedule. You'll need to set this  
flag on all slots in a schedule if you want the schedule to auto-repeat without  
the need for manual reset commands.  
  
This function can also be used to sneak special command slots into the schedule:  
If you specify a negative number for the 'bufferHandle' argument, then this  
actually defines a command slot instead of a regular playback slot, and the  
number is a command code that defines the action to take. For timing related  
actions, the 'repetitions' parameter is abused as a 'tWhen' time specification  
in seconds.  
Following command codes are currently defined: (Add numbers to combine options)  
1   = Pause audio playback (and capture) immediately, resume it at a given  
'tWhen' target time.  
2   = (Re-)schedule the end of playback for given 'tWhen' target time.  
You must specify the type of 'tWhen' if you specify 1 or 2 as commandCode:+4  =  
'tWhen' is an absolute [GetSecs](GetSecs)() style system time.  
+8  = 'tWhen' is a time delta to the last requested start time of playback.  
+16 = 'tWhen' is a time delta to the last actual start time of playback.  
+32 = 'tWhen' is a time delta to the last requested end time of playback. Broken  
& Defective!!  
+64 = 'tWhen' is a time delta to the last actual end time of playback. Broken &  
Defective!!  
  
E.g., you want to (re)start playback at a certain time, then you'd set  
'bufferHandle' to -5, because command code would be 1 + 4 == 5, so negated it is  
-5. Then you'd specify the requested time in the 'repetitions' parameter as an  
absolute time in seconds.  
  
  


###See also:
[FillBuffer](PsychPortAudio-FillBuffer) Start Stop [RescheduleStart](PsychPortAudio-RescheduleStart) [UseSchedule](PsychPortAudio-UseSchedule)
