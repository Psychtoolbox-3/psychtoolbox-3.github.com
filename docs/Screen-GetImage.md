# [Screen('GetImage')](Screen-GetImage) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Slowly copy an image from a window or texture to Matlab/Octave, by default  
returning a uint8 array.  
  
Calling this function on an onscreen window while an asynchronous flip is  
pending on the window due to [Screen](Screen)('AsyncFlipBegin') is not allowed. Finalize  
such flips first. Readback of other onscreen or offscreen windows or textures is  
possible during async flip, but discouraged because it will have a significant  
impact on performance.  
  
The returned imageArray by default has three layers, i.e. it is an RGB image.  
  
"windowPtr" is the handle of the onscreen window, offscreen window or texture  
whose image should be returned.  
  
"rect" is the rectangular subregion to copy, and its default is the whole  
window. The specified image subregion must be fully contained inside the window,  
otherwise this function will abort with an error.  
  
Matlab/Octave will complain if you try to do math on a uint8 array, so you may  
need to use DOUBLE to convert it, e.g. imageArray/255 will produce an error, but  
double(imageArray)/255 is ok. Also see [Screen](Screen) 'PutImage' and 'CopyWindow'.  
  
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
  
"floatprecision" If you set this optional flag to 1, the image data will be  
returned as a double precision matrix instead of a uint8 matrix. Please note  
that normal image data will be returned in the normalized range 0.0 to 1.0  
instead of 0 - 255. Floating point readback is only beneficial when reading back  
floating point precision textures, offscreen windows or the framebuffer when the  
imaging pipeline is active and HDR mode is selected (ie. more than 8bpc  
framebuffer). On [OpenGL](OpenGL)-ES hardware, only floating point framebuffers do support  
'floatprecision' readback.  
"nrchannels" Number of color channels to return. By default, 3 channels (RGB)  
are returned. Specify 1 for Red/Luminance only, 2 for Red+Green or  
Luminance+Alpha, 3 for RGB and 4 for RGBA. A setting of 2 is not supported on  
[OpenGL](OpenGL)-ES hardware.   
  
  


###See also:
[PutImage](Screen-PutImage) [CopyWindow](Screen-CopyWindow) [CreateMovie](Screen-CreateMovie) [FinalizeMovie](Screen-FinalizeMovie)
