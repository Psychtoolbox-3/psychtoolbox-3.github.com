# [Screen('SetMovieTimeIndex')](Screen-SetMovieTimeIndex) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Set current time index for movie object with handle 'moviePtr'.  
  
The new time index is specified in 'timeindex'. By default, or if the optional  
'indexIsFrames' flag is set to zero, 'timeindex' is in seconds of movie time. If  
'indexIsFrames' is set to 1, then 'timeindex' is interpreted as a frameindex in  
frames since start of movie, starting with frame 0 as the first frame in the  
movie.  
  
Specifying a new timeindex in seconds is usually faster than specifying a  
timeindex in frames.  
  
The function optionally returns the old position in seconds in the return  
argument 'oldtimeindex'.  
  


###See also:
[CloseMovie](Screen-CloseMovie) [PlayMovie](Screen-PlayMovie) [GetMovieImage](Screen-GetMovieImage) [GetMovieTimeIndex](Screen-GetMovieTimeIndex) [SetMovieTimeIndex](Screen-SetMovieTimeIndex)
