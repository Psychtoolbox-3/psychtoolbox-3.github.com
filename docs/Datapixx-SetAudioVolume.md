# [Datapixx('SetAudioVolume')](Datapixx-SetAudioVolume) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetAudioVolume', volume [, source=0]);

Set volume of audio playback. -"volume" can have two columns, or a single  
column. If it has two columns, then the first column specifies the volume of the  
Datapixx Audio Out 3.5mm stereo jack, and the second column specifies the volume  
of the Datapixx internal speaker. If the volume argument has a single column,  
then it sets the volume for both the stereo jack and the internal speaker. The  
volume argument can also have two rows, or a single row. If it has two rows,  
then the first row specifies the volume of the left ear channel, and the second  
row specifies the volume of the right ear channel. If the volume argument has a  
single row, then it sets the volume for both the left and right ears.  
The source argument can either be 0 or 1. The default value (0) changes the  
volume directly in the code.If you set the source to 1, then the [DATAPixx](DATAPixx) will  
implify the volume of the audio waveforms.   
If you need to mute the speakers you will need to mute with the source set to  
zero.   
  


###See also:
[InitAudio](Datapixx-InitAudio), [WriteAudioBuffer](Datapixx-WriteAudioBuffer), [StartAudioSchedule](Datapixx-StartAudioSchedule), [StopAudioSchedule](Datapixx-StopAudioSchedule), [GetAudioStatus](Datapixx-GetAudioStatus)
