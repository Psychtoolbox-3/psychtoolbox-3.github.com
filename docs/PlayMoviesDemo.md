# [PlayMoviesDemo](PlayMoviesDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[MovieDemos](MovieDemos)

[PlayMoviesDemo](PlayMoviesDemo)(moviename [, backgroundMaskOut][, tolerance][, pixelFormat=4][, maxThreads=-1])  
  
This demo accepts a pattern for a valid moviename, e.g.,  
moviename=`\*.mpg`, then it plays all movies in the current working  
directory whose names match the provided pattern, e.g., the `\*.mpg`  
pattern would play all MPEG files in the current directory.  
  
If you don't specify a moviename, the demo will ask you if it should play  
our standard [DualDiscs](DualDiscs).mov demo movie, or rather play through a set of  
videos in a playlist which are streamed from the internet. These 'c'ool  
videos may provide you with useful information for your daily work.  
  
This demo uses automatic asynchronous playback for synchronized playback  
of video and sound. Each movie plays until end, then rewinds and plays  
again from the start. Pressing the Cursor-Up/Down key pauses/unpauses the  
movie and increases/decreases playback rate.  
The left- right arrow keys jump in 1 seconds steps. SPACE jumps to the  
next movie in the list. ESC ends the demo.  
  
If the optional RGB color vector backgroundMaskOut is provided, then  
color pixels in the video which are equal or close to backgroundMaskOut will be  
discarded during drawing. E.g., backgroundMaskOut = [255 255 255] would  
discard all white pixels, backgroundMaskOut = [0 0 0] would discard all  
black pixels etc. The optional tolerance parameter allows for some  
lenience, e.g., tolerance = 10 would discard all pixels whose euclidean  
distance in RGB color space is less than 10 units to the backgroundMaskOut  
color. Background color masking requires a graphics card with fragment  
shader support and will fail otherwise.  
  
If the optional `pixelFormat` is specified, it is used to choose  
optimized video playback methods for specific content. Valid values are 1  
or 2 for greyscale video playback, and 7 or 8 for optimized grayscale  
video playback on modern GPU's with GLSL shading support. Values 3, 4, 5  
and 6 play back color video. 4 is the default, 5 or 6 may provide  
significantly improved playback performance on modern [GPUs](GPUs).  
  
If the optional `maxThreads` is specified, it defines the maximum number  
of parallel processing threads that should be used by multi-threaded  
video codecs for playback. A setting of n selects n threads, a setting of  
zero asks to auto-select an optimum number of threads for a given  
computer. By default, a codec specific default number is used, typically  
one thread.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MovieDemos/PlayMoviesDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MovieDemos/PlayMoviesDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MovieDemos/PlayMoviesDemo.m</code>
</div>

