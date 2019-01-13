# [Screen('AddAudioBufferToMovie')](Screen-AddAudioBufferToMovie) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

Screen('AddAudioBufferToMovie', moviePtr, audioBuffer);

Add a buffer filled with audio data samples to movie 'moviePtr'.  
The movie must have been created in 'CreateMovie' with an options string that  
enables writing of an audio track into the movie, otherwise this function will  
fail.  
You enable writing of audio tracks by adding the keyword 'AddAudioTrack' to the  
options string.  
Alternatively, if your options string is a gst-launch style pipeline  
description, it must contain one pipeline element with a name option of  
'name=ptbaudioappsrc'.  
'audioBuffer' must be 'numChannels' rows by 'numSamples' columns double matrix  
of audio data. Each row encodes one audio channel, each column element in a row  
encodes a sample. E.g., a 2-by-48000 matrix would encode 48000 samples for a two  
channel stereo sound track.  
[Sample](Sample) values must lie in the range between -1.0 and +1.0.  
The audio buffer is converted into a movie specific sound format and then  
appended to the audio samples already stored in the audio track.  
  
  


###See also:
[FinalizeMovie](Screen-FinalizeMovie) [AddFrameToMovie](Screen-AddFrameToMovie) [CloseMovie](Screen-CloseMovie) [PlayMovie](Screen-PlayMovie) [GetMovieImage](Screen-GetMovieImage) [GetMovieTimeIndex](Screen-GetMovieTimeIndex) [SetMovieTimeIndex](Screen-SetMovieTimeIndex)
