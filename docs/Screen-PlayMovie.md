# [Screen('PlayMovie')](Screen-PlayMovie) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[droppedframes] = Screen('PlayMovie', moviePtr, rate, [loop], [soundvolume]);

Start playback of movie associated with movieobject 'moviePtr'. 'rate' defines  
the desired playback rate: 0 == Stop playback, 1 == Normal speed forward, -1 ==  
Normal speed backward, ... . Not all movie files allow reverse playback or  
playback at other rates than normal speed forward. 'loop' Enable looped playback  
if set to a value greater than zero. A value of 1 will enable repetitive looped  
playback with the default strategy, or the special strategy selected via the  
optional 'specialFlags1' settings provided during the call to  
[Screen](Screen)('OpenMovie', ...). Values greater than 1 select different repetition  
strategies when combined together. Different strategies exist to handle  
different quirks with some movie file formats and encodings and with some  
versions of [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)): A flag of 2 requests looped playback via gapless  
reloading of the movie instead of rewinding it to the start. A flag of 1+4 uses  
so called segment seeks for rewinding, whereas adding 8 (e.g., 1+8 or 1+4+8)  
asks to flush the video pipeline during rewinding. Your mileage with these  
looping strategies will differ, but usually the default settings are good enough  
for most purposes. There are however movie files or network video streams that  
can't be automatically repeated at all, so called non-seekable streams.  
'soundvolume' Select the output audio volume of an associated soundtrack: 0 =  
Mute sound output, 0.01 - 1.0 Volume in percent. You can choose the sound volume  
with low overhead while playback is active by calling this function, as long as  
you provide the same parameters for all other settings as the ones you used when  
starting playback, ie. only 'soundvolume' may differ.  
If the function is called to stop playback, it will return the number of frames  
that needed to be dropped in order to keep video playback in sync with realtime  
and audio playback. Otherwise it returns zero.  
  


###See also:
[CloseMovie](Screen-CloseMovie) [PlayMovie](Screen-PlayMovie) [GetMovieImage](Screen-GetMovieImage) [GetMovieTimeIndex](Screen-GetMovieTimeIndex) [SetMovieTimeIndex](Screen-SetMovieTimeIndex)
