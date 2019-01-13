# [Datapixx('SetAudioVolume')](Datapixx-SetAudioVolume) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetAudioVolume', volume);

Set volume of audio playback. -"volume" can have two columns, or a single  
column. If it has two columns, then the first column specifies the volume of the  
Datapixx Audio Out 3.5mm stereo jack, and the second column specifies the volume  
of the Datapixx internal speaker. If the volume argument has a single column,  
then it sets the volume for both the stereo jack and the internal speaker. The  
volume argument can also have two rows, or a single row. If it has two rows,  
then the first row specifies the volume of the left ear channel, and the second  
row specifies the volume of the right ear channel. If the volume argument has a  
single row, then it sets the volume for both the left and right ears.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [WriteAudioBuffer](Datapixx-WriteAudioBuffer), [StartAudioSchedule](Datapixx-StartAudioSchedule), [StopAudioSchedule](Datapixx-StopAudioSchedule), [GetAudioStatus](Datapixx-GetAudioStatus)
