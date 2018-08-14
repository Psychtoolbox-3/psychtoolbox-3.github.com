# [Datapixx('ReadDinLog')](Datapixx-ReadDinLog) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Upload digital input data from a Datapixx internal log buffer to the local host.  
-"numFrames" is the number of frames to upload, and should not exceed  
newLogFrames returned by [GetDinStatus](GetDinStatus). If numFrames argument is missing,  
[ReadDinLog](ReadDinLog) will return all remaining logged data.  
-"logData" is a row vector of acquired digital input values. Each column of the  
vector contains an unsigned integer with the new state of digital inputs 0 to 15  
after a transition.  
-"logTimetags" is a row vector of acquisition timetags, indicating when the  
corresponding transition to the state in logData occurred. The timetags are in  
double precision seconds since Datapixx powerup. Response times can be  
calculated by calling [SetMarker](SetMarker)() at stimulus onset, then subtracting  
[GetMarker](GetMarker)() from the logged timetags.  
-"underflow" is set to 1 if calls to [ReadDinLog](ReadDinLog) read too many frames. The  
newLogFrames field returned by [GetDinStatus](GetDinStatus) indicates the maximum number of  
frames which can be read by [ReadDinLog](ReadDinLog). If more than this number of frames is  
read, an underflow occurs and there will be errors in the logged data. In  
addition to returning an underflow flag, the numLogUnderflows field returned by  
[GetDinStatus](GetDinStatus) will be incremented.  
See [DatapixxSimonGame](DatapixxSimonGame), [DatapixxDin](DatapixxDin)\*Demo files for examples.  
  


###See also:
[SetDinLog](Datapixx-SetDinLog), [StartDinLog](Datapixx-StartDinLog), [StopDinLog](Datapixx-StopDinLog), [GetDinStatus](Datapixx-GetDinStatus)
