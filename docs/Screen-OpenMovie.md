# [Screen('OpenMovie')](Screen-OpenMovie) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[ moviePtr [duration] [fps] [width] [height] [count] [aspectRatio] [hdrStaticMetaData]]=Screen('OpenMovie', windowPtr, moviefile [, async=0] [, preloadSecs=1] [, specialFlags1=0][, pixelFormat=4][, maxNumberThreads=-1][, movieOptions]);

Try to open the multimediafile 'moviefile' for playback in onscreen window  
'windowPtr' and return a handle 'moviePtr' on success.  
This function requires the [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) multi-media framework to be installed on  
your system.  
The following movie properties are optionally returned: 'duration' Total  
duration of movie in seconds. 'fps' Video playback framerate, assuming a linear  
spacing of videoframes in time. There may exist exotic movie formats which don't  
have this linear spacing. In that case, 'fps' would return bogus values and the  
check for skipped frames would report bogus values as well. 'width' Width of the  
images contained in the movie. 'height' Height of the images.  
'count' Total number of videoframes in the movie. Determined by counting, so  
querying 'count' can significantly increase the execution time of this command.  
'aspectRatio' Pixel aspect ratio of pixels in the video frames. Typically 1.0  
for square pixels.  
'hdrStaticMetaData' A struct with HDR static metadata of the movie, if the movie  
has HDR metadata attached and your system supports parsing of HDR metadata. This  
requires [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) version 1.18 or later, and note that not all video codecs may  
support parsing of HDR metadata.  
hdrStaticMetaData.Valid is 1 if the movie has HDR metadata, 0 if none is  
available or parsing is not supported by your system. All other returned HDR  
properties are compatible with (and in the format of) the function  
[PsychHDR](PsychHDR)('HDRMetadata'). Type 'PsychHDR [HDRMetadata](HDRMetadata)?' for details.  
The structure also reports some fields reported by [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) movie codecs, but  
not exclusive to HDR movies: 'Colorimetry', 'LimitedRange', 'YUVRGBMatrixType',  
'PrimariesType', 'EOTFType', 'Format', and 'Depth'.  
If you want to play multiple movies in succession with lowest possible delay  
inbetween the movies then you can ask PTB to load a movie in the background  
while another movie is still playing: Call this function with the 'async' flag  
set to 1. This will initiate the background load operation. After some  
sufficient time has passed, you can call the 'OpenMovie' function again, this  
time with the 'async' flag set to zero. Now the function will return a valid  
movie handle for playback.  
If all your movies have exactly the same format and only differ in duration and  
content, but not in image size, color depth, encoding format, or fps, then you  
can also use an aync setting of 2 and provide the 'moviePtr' handle of an  
already opened movie in the 'preloadSecs' parameter. This will queue the movie  
'moviefile' as a successor to the currently playing moviefile in 'moviePtr'.  
Queuing movies this way is more efficient than async flag setting 1, although  
also more restricted.  
If the 'async' flag also contains the number 4 or is equal to 4, then movie  
playback will not automatically drop video frames to preserve audio-video sync  
in case fetching and display of video frames by your script is delayed or too  
slow. This has the disadvantage that you'll need to take care of audio-video  
sync and framerate control yourself by proper comparison of movie presentation  
timestamps and [GetSecs](GetSecs) or [Screen](Screen)('[Flip](Flip)') timestamps. The advantage is, that  
after start of playback the playback engine can internally predecode and buffer  
up to 'preloadSecs' seconds worth of video and audio data. This may allow  
complex movies to play more smoothly or at higher framerates.  
'preloadSecs' This optional parameter allows to ask [Screen](Screen)() to buffer at least  
up to 'preloadSecs' seconds of the movie. This potentially allows for more  
stutter-free playback, but your mileage may vary, depending on movie format,  
storage medium and lots of other factors. In most cases, the default setting is  
perfectly sufficient. The special setting -1 means: Try to buffer the whole  
movie. Caution: Long movies may cause your system to run low on memory or disc  
space and have disastrous effects on playback performance! Also, the exact type  
of buffering applied depends a lot on the movie playback engine and movie  
format, but it usually affects the buffering behaviour and capacity of buffering  
in some meaningful way.  
'specialFlags1' Optional flags, numbers to be added together: 1 = Use YUV video  
decoding instead of RGBA, if supported by movie codec and GPU - May be more  
efficient. 2 = Don't decode and use sound - May be more efficient. On Linux you  
may need to specify a setting of 2 if you try to use movie playback at the same  
time as [PsychPortAudio](PsychPortAudio) sound output, otherwise movie playback may hang. A flag  
of 4 will try to disable gpu hardware accelerated video decoding for playback of  
this and all future movies for the running Octave/Matlab session. A flag of 8  
will ask the video decoder to skip all B-Frames during decoding to reduce  
processor load on very slow machines. Not all codecs may support flag 8, in  
which case these flags are silently ignored. A flag of 16 asks [Screen](Screen) to convert  
all video textures immediately into a format which makes them useable as  
offscreen windows, and for the [Screen](Screen)('TransformTexture') function as well as  
for drawing them with your own custom GLSL shaders. Normally this conversion  
would be deferred until needed, ie. it would get skipped if you would just draw  
the texture regularly. If you know already that you want to use the texture with  
one of the given functions, manually triggering the conversion via this flag may  
be a bit more efficient - or convenient if you want to use your own GLSL  
shaders.  
The optional flags 32, 64 and 128 influence how looped playback is performed if  
usercode requests such repetitive playback via [Screen](Screen)('PlayMovie', ...) with the  
'loop' flag set to one. Different strategies exist to handle different quirks  
with some movie file formats and encodings and some versions of [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)): A  
flag of 32 requests looped playback via gapless reloading of the movie instead  
of rewinding it to the start. A flag of 64 uses so called segment seeks for  
rewinding, a flag of 128 asks to flush the video pipeline during rewinding. Your  
mileage with these looping strategies will differ, but usually the default  
settings are good enough for most purposes.  
A 'specialFlags1' setting of 256 will prevent automatic deinterlacing of video.  
This is useful to prevent some internal color data conversions, e.g., of pure  
grayscale data, which can cause slightly lossy decoding of lossless video data.  
A 'specialFlags1' setting of 512 marks the movie as encoded in Psychtoolbox's  
own proprietary 16 bpc high precision format. Grayscale movies in this format  
can be created by specifying the keyword [UsePTB16BPC](UsePTB16BPC) in [Screen](Screen)('CreateMovie') or  
in the firewire videocapture engine as part of the codec spec string. RGB movies  
can also get created this way. Encoding or decoding of such 16 bpc movies with a  
channel count other than 1 or 3 for gray or RGB is not supported.  
A 'specialFlags1' setting of 1024 tells the movie playback that this movies  
video frames are encoded as raw Bayer sensor data and that they should get  
converted to RGB images during playback via software Bayer filtering. You must  
set the 'pixelFormat' parameter to 1 for this to work. You can choose the Bayer  
filtering method via 'DebayerMethod' setting and the color sensor filter pattern  
via 'OverrideBayerPattern' setting in [Screen](Screen)('SetVideoCaptureParameter', -1,  
...). By default, fast nearest neighbour debayering with an assumed sensor image  
layout of RGGB is performed.  
'pixelFormat' optional argument specifying the pixel format of decoded video  
frames. Not all possible valid values are supported by all video codecs,  
graphics cards and operating systems. If an unsupported format is requested,  
[Screen](Screen)() will try to choose the closest matching format that meets or exceeds  
the specified format, at a performance or efficiency penalty. If no sufficiently  
close match is possible without severely degraded performance or other  
restrictions, the function will abort with an error. The following formats are  
supported on some setups: 1 = Luminance/Greyscale image, 2 = Luminance+Alpha, 3  
= RGB 8 bit per channel, 4 = RGBA8, 5 = YUV 4:2:2 packed pixel format on some  
graphics hardware, 6 = YUV-I420 planar format, using GLSL shaders for color  
space conversion on suitable graphics cards. 7 or 8 = Y8-Y800 planar format,  
using GLSL shaders, 9 = 16 bit Luminance, 10 = 16 bpc RGBA image, 11 = 16 bpc  
RGB image for proper encoding of HDR/WCG content, e.g., video encoded in HDR-10  
format for display on a HDR display. The always supported default is '4' ==  
RGBA8 format when the onscreen window is in standard dynamic range (SDR) mode.  
If 'windowPtr' instead refers to a HDR display window, displaying on a HDR  
display monitor, then the default setting for 'pixelFormat' is '11' == RGB  
format for proper HDR movie display with up to 16 bpc precision and proper  
handling of HDR transfer function like Perceptual Quantizer (PQ) and HDR color  
spaces.  
A setting of 6 (for color) or 7/8 (for grayscale) for selection of  
YUV-I420/Y8-Y800 format, as supported by at least the H264 and [HuffYUV](HuffYUV) video  
codecs on any GPU with shader support, can be especially efficient for fast  
playback of high resolution video. As this format uses shaders for  
post-processing, it should be fast for texture drawing, but can incur  
significant overhead if you try to draw into a texture of this format, or try to  
post-process it via [Screen](Screen)('TransformTexture'). If you try to attach your own  
shaders to such a texture during [Screen](Screen)('DrawTexture'), you will need to  
implement color conversion yourself in your shaders, as your shaders would  
override [Screen](Screen)'s builtin color conversion shader.  
'maxNumberThreads' Optional parameter which allows to set the maximum number of  
parallel processing threads that should be used by multi-threaded video codecs  
to decode the movie. The parameter has no effect on single threaded codecs and  
default behaviour is to let the codec do whatever it wants. A setting of zero  
tells the codec to use multi-threaded decoding with a number of threads that is  
auto-selected to be optimal for your given computer. A number n greater zero  
asks the codec to use at most n threads for decoding. The most safe choice is to  
not specify this parameter - this should work even with problematic movie  
formats. If you need higher playback performance, e.g., for high resolution  
video or high framerate playback, you should set the parameter to zero to allow  
the optimal choice to the video codec. This should work flawlessly with well  
encoded high quality movie files and can provide a significant performance boost  
on multi-core computers. Specify a discrete non-zero number of threads if you  
want to benefit from multi-core decoding but want to prevent movie playback from  
using up all available computation power, e.g., because you want to run some  
other timing-sensitive tasks in parallel and want to make sure to leave some  
processor cores dedicated to them.  
'movieOptions' Optional text string which encodes additional options for  
playback of the movie. Parameters are keyword=value pairs, separated by three  
colons ::: if there are multiple parameters. Currently supported keywords:  
[OverrideEOTF](OverrideEOTF)=eotfID -- Override detected EOTF transfer function of movie to  
instead be of type eotfID. E.g., specifying [OverrideEOTF](OverrideEOTF)=14 would select  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) EOTF type 14, which is GST\_VIDEO\_TRANSFER\_SMPTE2084 == HDR PQ  
function, whereas [OverrideEOTF](OverrideEOTF)=15 would select [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) EOTF type 15, which is  
GST\_VIDEO\_TRANSFER\_ARIB\_STD\_B67 == HDR HLG function. Please note that  
[OverrideEOTF](OverrideEOTF) is only accepted at the moment for playback with pixelFormat 11,  
otherwise it is rejected.  
You rarely need this override, unless you try to play back a movie format on a  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) version too old to detect the proper EOTF. Most likely if you try to  
play back HDR content on a [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) version older than 1.18.0.  
[AudioSink](AudioSink)=[GStreamerSinkSpec](GStreamerSinkSpec) -- [GStreamerSinkSpec](GStreamerSinkSpec) is a [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) gst-launch line  
style specification for a audio sink plugin and its parameters. This allows to  
customize where the audio of a movie is sent during playback and with which  
parameters. By default, the autoaudiosink plugin is used, which automatically  
chooses audio output and parameters, based on your system and user settings.  
Most often this is what you want. Sometimes you may want to have more control  
over outputs, e.g., if your system has multiple sound cards installed and you  
want to route audio output to a specific card and output connector. Example use  
of the parameter: 'AudioSink=pulseaudiosink device=MyCardsOutput1' would use the  
Linux pulseaudiosink plugin to send sound data to the output named  
'MyCardsOutput1' via the [PulseAudio](PulseAudio) sound server commonly used on Linux desktop  
systems.  
If you set a [Screen](Screen)() verbosity level of 4 or higher, [Screen](Screen)() will print out  
the actually used audio output at the end of movie playback on operating systems  
which support this. This can help debugging issues with audio routing if you  
don't hear sound.  
  


###See also:
[CloseMovie](Screen-CloseMovie) [PlayMovie](Screen-PlayMovie) [GetMovieImage](Screen-GetMovieImage) [GetMovieTimeIndex](Screen-GetMovieTimeIndex) [SetMovieTimeIndex](Screen-SetMovieTimeIndex)
