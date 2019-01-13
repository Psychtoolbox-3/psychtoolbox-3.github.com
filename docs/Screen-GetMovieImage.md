# [Screen('GetMovieImage')](Screen-GetMovieImage) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[ texturePtr [timeindex]]=Screen('GetMovieImage', windowPtr, moviePtr, [waitForImage=1], [fortimeindex], [specialFlags = 0] [, specialFlags2 = 0]);

Try to fetch a new texture image from movie object 'moviePtr' for visual  
playback/display in onscreen window 'windowPtr' and return a texture-handle  
'texturePtr' on successfull completion. 'waitForImage' If set to 1 (default),  
the function will wait until the image becomes available. If set to zero, the  
function will just poll for a new image. If none is ready, it will return a  
texturePtr of zero, or -1 if none will become ready because movie has reached  
its end and is not in loop mode.  
'fortimeindex' Don't request the next image, but the image closest to time  
'fortimeindex' in seconds. 'fortimeindex' is only used if either playback is  
stopped in any case, or if forward playback is active while using the [[GStreamer](GStreamer)][(GStreamer)]((GStreamer))  
playback engine and fetching video frames asynchronously due to opening the  
movie with async flag set and sufficient buffering enabled on suitable movie  
file formats. In all other cases the 'fortimeindex' is silently ignored.  
Therefore you should always check if the timestamp of the returned movie frame  
actually satisfies the given 'fortimeindex' value if you choose to use  
'fortimeindex'.  
The (optional) return value 'timeindex' contains the exact time when the  
returned image should be displayed wrt. to the start of the movie - a  
presentation timestamp.   
'specialFlags' (optional) encodes special requirements for the returned texture.  
A setting of 1 will try to create the texture as a GL\_TEXTURE\_2D texture.  
However this is not well supported with a setting of 2 (see below) or with use  
of a special 'pixelFormat' \> 4 in [Screen](Screen)('OpenMovie'). A setting of 2 will  
request that the texture is prepared for drawing it with highest possible  
spatial precision. See explanation of 'specialFlags' == 2 in  
[Screen](Screen)('MakeTexture') for details. A 'specialFlags' == 8 will prevent automatic  
mipmap-generation for GL\_TEXTURE\_2D textures. A 'specialflags' == 32 will  
prevent closing the texture by a call to [Screen](Screen)('[Close](Close)');  
'specialFlags2' (optional) More special flags: A setting of 1 tells the function  
to not return presentation timestamps in 'timeindex'. This means that  
'timeindex' will be always returned as zero and that the built-in detector for  
skipped frames is disabled as well. This may (or may not) save a little bit of  
computation time during playback of very demanding movies on lower end systems,  
your mileage will vary, depending on many factors.  
A setting of 2 will skip creation and return of an actual video texture, instead  
a texture handle of 1 will be returned and no texture gets created. This is  
useful for fast fine-grained forward seeking in the movie by skipping single  
frames, and for benchmarking.  
  


###See also:
[CloseMovie](Screen-CloseMovie) [PlayMovie](Screen-PlayMovie) [GetMovieImage](Screen-GetMovieImage) [GetMovieTimeIndex](Screen-GetMovieTimeIndex) [SetMovieTimeIndex](Screen-SetMovieTimeIndex)
