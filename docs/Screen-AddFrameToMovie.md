# [Screen('AddFrameToMovie')](Screen-AddFrameToMovie) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

Screen('AddFrameToMovie', windowPtr [,rect] [,bufferName] [,moviePtr=0] [,frameduration=1])

Get an image from a window or texture and add it as a new video frame to a  
movie.  
  
Calling this function on an onscreen window while an asynchronous flip is  
pending on the window due to [Screen](Screen)('AsyncFlipBegin') is not allowed. Finalize  
such flips first. Readback of other onscreen or offscreen windows or textures is  
possible during async flip, but discouraged because it will have a significant  
impact on performance.  
  
"windowPtr" is the handle of the onscreen window, offscreen window or texture  
whose image should be added.  
  
"rect" is the rectangular subregion to get, and its default is the whole window.  
The function will only honor the top-left corner of the 'rect' argument, but  
ignore the bottom-right corner and thereby the width and height as defined by  
the 'rect'. The size of added video frames is fully defined as the fixed size of  
movie frames as specified at movie creation time via the [Screen](Screen)('CreateMovie')  
call. The specified image region must be fully contained inside the window.  
  
"bufferName" is a string specifying the buffer from which to copy the image: The  
'bufferName' argument is meaningless for offscreen windows and textures and will  
be silently ignored. For onscreen windows, it defaults to 'frontBuffer', i.e.,  
it returns the image that is sent through the video output of your graphics card  
to your display device at that moment. On [OpenGL](OpenGL)-ES graphics hardware, all  
'bufferName' settings except 'backBuffer' or 'drawBuffer' will be ignored and  
image data is always read from either the 'drawBuffer' or the 'backBuffer'. This  
is an unavoidable system limitation of such embedded hardware.  
If frame-sequential stereo mode is enabled, 'frontLeftBuffer' returns the image  
generated for the left eye, 'frontRightBuffer' returns the right-eye view. If  
double-buffering is enabled, you can also return the 'backBuffer', i.e. what  
your subject will see after the next [Screen](Screen)('[Flip](Flip)') command, and for  
frame-sequential stereo also 'backLeftBuffer' and 'backRightBuffer'  
respectively. Both the 'frontBuffer' and 'backBuffer' images and their stereo  
variants will return the final images as they are really encoded in the system  
framebuffer and sent to the video outputs of your graphics hardware. These  
images are the result of any post-processing done by the Psychtoolbox imaging  
pipeline, e.g., Retina display processing, geometric transformations, color  
transformations, certain types of gamma correction, stereo post-processing, or  
special pixel encoding for devices like Bits\# or Datapixx. As such they may  
differ in size and format from what you have drawn into the onscreen window.  
'aux0Buffer' - 'aux3Buffer' returns the content of [OpenGL](OpenGL) AUX buffers 0 to 3.  
Only query the AUX buffers if you know what you are doing, otherwise your script  
will crash. This is mostly meant for internal debugging of PTB.  
If the imaging pipeline is enabled, you can also return the content of the  
unprocessed backbuffer, ie. before processing by the pipeline, by requesting  
'drawBuffer'.  
If the imaging pipeline is enabled, querying the 'backBuffer' will only give you  
up to date results after you called [Screen](Screen)('[Flip](Flip)') or [Screen](Screen)('AsyncFlipBegin')  
or [Screen](Screen)('DrawingFinished'), otherwise you may encounter stale results. If our  
own homegrown frame-sequential stereo mode is in use, querying the  
'backLeftBuffer' and 'backRightBuffer' is well defined, after a [Screen](Screen)('[Flip](Flip)')  
or [Screen](Screen)('DrawingFinished'), but querying the 'frontLeftBuffer' or  
'frontRightBuffer' or 'frontBuffer' will result in an assignment of left- and  
right- stereo images that is mostly based on chance, e.g., you may get  
accidentally swapped left- and rightBuffer images!  
  
"moviePtr" is the optional handle to the movie to which the video frame should  
be added. You can get this handle from the [Screen](Screen)('CreateMovie') function when  
creating the movie. By default frames are added to the first movie created with  
[Screen](Screen)('CreateMovie').  
  
"frameduration" optionally defines the display duration of the added video frame  
in units of movie frame intervals. See the help for 'CreateMovie' for further  
explanation of "frameduration".  
  
Movie images are stored with 8 bits or 16 bits resolution per pixel color  
component. Images are stored as one (RED), three (RGB) or four channel (RGBA)  
frames. The number of channels and bitdepth is selected in the  
[Screen](Screen)('CreateMovie') call and then kept fixed throughout the movie. [OpenGL](OpenGL)-ES  
hardware only supports 8 bit storage in RGB or RGBA. Not all video codecs allow  
for lossless encoding or encoding of all color channels.  
  
See [Screen](Screen)('CreateMovie?') for help on movie creation.  
  


###See also:
[PutImage](Screen-PutImage) [CopyWindow](Screen-CopyWindow) [CreateMovie](Screen-CreateMovie) [FinalizeMovie](Screen-FinalizeMovie)
