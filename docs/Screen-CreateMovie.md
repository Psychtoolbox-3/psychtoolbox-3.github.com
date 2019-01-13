# [Screen('CreateMovie')](Screen-CreateMovie) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

moviePtr = Screen('CreateMovie', windowPtr, movieFile [, width][, height][, frameRate=30][, movieOptions][, numChannels=4][, bitdepth=8]);

Create a new movie file with filename 'movieFile' and according to given  
'movieOptions'.  
The function returns a handle 'moviePtr' to the file.  
Currently only single-track video encoding is supported.  
See '[Screen](Screen) [AddAudioBufferToMovie](AddAudioBufferToMovie)?' on how to add audio tracks to movies.  
  
Movie creation is a 3 step procedure:  
1. Create a movie and define encoding options via 'CreateMovie'.  
2. Add video and audio data to the movie via calls to 'AddFrameToMovie' et al.  
3. Finalize and close the movie via a call to 'FinalizeMovie'.  
  
### All following parameters are optional and have reasonable defaults:  
  
'width' Width of movie video frames in pixels. Defaults to width of window  
'windowPtr'.  
'height' Height of movie video frames in pixels. Defaults to height of window  
'windowPtr'.  
'frameRate' Playback framerate of movie. Defaults to 30 fps. Technically this is  
not the playback framerate but the granularity in 1/frameRate seconds with which  
the duration of a single movie frame can be specified. When you call  
'AddFrameToMovie', there's an optional parameter 'frameDuration' which defaults  
to one. The parameter defines the display duration of that frame as the fraction  
'frameDuration' / 'frameRate' seconds, so 'frameRate' defines the denominator of  
that term. However, for a default 'frameDuration' of one, this is equivalent to  
the 'frameRate' of the movie, at least if you leave everything at defaults.  
  
'movieoptions' a textstring which allows to define additional parameters via  
keyword=parm pairs. For [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) movie writing, you can provide the same  
options as for [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) video recording. See 'help VideoRecording' for  
supported options and tips.  
Keywords unknown to a certain implementation or codec will be silently ignored:  
[EncodingQuality](EncodingQuality)=x Set encoding quality to value x, in the range 0.0 for lowest  
movie quality to 1.0 for highest quality. Default is 0.5 = normal quality. 1.0  
often provides near-lossless encoding.  
'numChannels' Optional number of image channels to encode: Can be 1, 3 or 4 on  
[OpenGL](OpenGL) graphics hardware, and 3 or 4 on [OpenGL](OpenGL)-ES hardware. 1 = Red/Grayscale  
channel only, 3 = RGB, 4 = RGBA. Please note that not all video codecs can  
encode pure 1 channel data or RGBA data, ie. an alpha channel. If an unsuitable  
codec is selected, movie writing may fail, or unsupported channels (e.g., the  
alpha channel) may get silently discarded. It could also happen that a codec  
which doesn't support 1 channel storage will replicate the Red/Grayscale data  
into all three RGB channels, leading to no data loss but increased movie file  
size. Default is to request RGBA 4 channel data from the system, encoding to  
RGBA or RGB, depending on codec.  
'bitdepth' Optional color/intensity resolution of each channel: Default is 8  
bpc, for 8 bit per component storage. [OpenGL](OpenGL) graphics hardware, but not  
[OpenGL](OpenGL)-ES, also supports 16 bpc image readback. However, not all codecs can  
encode with \> 8 bpc color/luminance precision, so encoding with 16 bpc may fail  
or silently reduce precision to less bits, possibly 8 bpc or less. If you  
specify the special keyword [UsePTB16BPC](UsePTB16BPC) in 'movieoptions', then PTB will use its  
own proprietary 16 bpc format for 1 or 3 channel mode. This format can only be  
read by PTB's own movie playback functions, not by other software.  
In general, embedded [OpenGL](OpenGL)-ES graphics hardware is more restricted in the type  
of image data it can return. Most video codecs are lossy codecs. They will  
intentionally throw away color or spatial precision of encoded video to reduce  
video file size or network bandwidth, often in a way that is not easily  
perceptible to the naked eye. If you require high fidelity, make sure to  
double-check your results for a given codec + parameter setup, e.g., via  
encoding + decoding the movie and checking the original data against decoded  
data.  
  
  


###See also:
[FinalizeMovie](Screen-FinalizeMovie) [AddFrameToMovie](Screen-AddFrameToMovie) [CloseMovie](Screen-CloseMovie) [PlayMovie](Screen-PlayMovie) [GetMovieImage](Screen-GetMovieImage) [GetMovieTimeIndex](Screen-GetMovieTimeIndex) [SetMovieTimeIndex](Screen-SetMovieTimeIndex)
