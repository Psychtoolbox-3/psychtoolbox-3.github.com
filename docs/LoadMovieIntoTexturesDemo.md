# [LoadMovieIntoTexturesDemo](LoadMovieIntoTexturesDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[MovieDemos](MovieDemos)

  
[LoadMovieIntoTexturesDemo](LoadMovieIntoTexturesDemo)(moviename [, fromTime=0][, toTime=end][, indexisFrames=0][, benchmark=0][, async=0][, preloadSecs=1][, specialflags=0][, pixelFormat=4])  
  
A demo implementation on how to load a movie into standard  
Psychtoolbox textures for precisely controlled presentation timing and  
presentation order.  
  
Parameters:  
moviename - Filename of moviefile to use. If none is provided, then the  
simple [DualDiscs](DualDiscs) collision movie is used which is part of PTB.  
  
fromTime - Start time (in seconds) from which the movie should be read  
into textures. Defaults to start of movie, if not provided.  
  
toTime - End time (in seconds) upto which the movie should be read  
into textures. Defaults to end of movie, if not provided.  
  
indexIsFrames - If set to 1 then the fromTime and toTime parameters are  
interpreted as frameindex (starting with 0 for the first frame), instead  
of seconds. If set to 2 then presentation timestamps are ignored for the  
decision when to stop loading a movie. This is needed for certain movies  
with a broken encoding of time, as those would stop loading way too early  
otherwise.  
  
benchmark - If you set this parameter to 1, the demo will compute the  
time it takes to load the movie, and - after the movie has been loaded  
into textures - the maximum display speed without syncing to vertical  
refresh. All visual progress feedback is disabled. This is mostly  
useful to benchmark different movie file formats and codecs for their  
relative efficiency on a given machine. A setting of 2 will additionally  
disable test of abort keys during loading of the movie - to discount  
possible pollution of the benchmark results with time spent checking the  
keyboard. A setting of 3 will also skip keyboard queries during the load  
phase, additionally it will not queue up textures in video memory, but  
instead load a texture and then immediately discard it. This is more  
resembling typical movie playback, where a frame is pulled, presented on  
screen, then discarded. It tests a different decoding path in [Screen](Screen)(). A  
setting of 4 will only test decoding performance of the movie, but omit  
creation of actual Psychtoolbox textures for presentation. This allows to  
separate computation time spent in the video decoder from time consumed  
by the graphics driver or graphics card.  
  
async - If you set this parameter to 4, the video decoding engine will  
prebuffer frames ahead of time, up to 'preloadSecs' seconds worth of  
video data. This is unsuitable for playback with audio-video sync, but  
for pure video playback it can decouple decoding from presentation  
further and provide a potential performance boost for very demanding  
playback scenarios.  
  
preloadSecs - How many seconds of video to prebuffer if async == 4?  
Specify a maximum amount in seconds, or the value -1 for unlimited  
prebuffering.  
  
specialflags - Special flags for 'OpenMovie'. E.g., a setting of 1 will  
try to use YUV textures for higher performance, if the installed graphics  
card supports this. A setting of 4 will always use YUV decoding, by use  
of out own builtin YUV decoder, which may be more limited in  
functionality and flexibility, but helpful if highest performance is a  
requirement.  
  
pixelFormat - Format of video texture to create: 1 = Luminance/Grayscale  
only, 2 = Luminance+Alpha, 3 = RGB color, 4 = RGBA, 5 = YUV-422 packed  
pixel, 6 = YUV-I420 planar format. 5 and 6 = Y8-Y800 planar luminance  
only format. Not all formats are supported by all GPU's, operating  
systems and video codecs. Defaults to 4 = RGBA 8 Bit per color channel.  
  
  
How the demo works: Read the source code - its well documented ;-)  
  
This demo "preloads" the movie into textures:  
The whole movie gets read into PTB textures before start of trial. Then  
you show the textures in quick succession like in [PlayMoviesDemo](PlayMoviesDemo). The  
advantage of this approach is exact control over display timing and  
display order: You can show frames in any order you like at any rate you  
like (and that your hardware likes). Disadvantage: Longer trial  
setup time for loading the whole movie, higher memory consumption (keep  
all n frames in memory instead of only the current one) and the inability  
to play sound in sync with video.  
  
To make it a bit more interesting, you can use this demo to "browse" short  
videoclips, e.g., for selection of interesting parts...  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MovieDemos/LoadMovieIntoTexturesDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MovieDemos/LoadMovieIntoTexturesDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MovieDemos/LoadMovieIntoTexturesDemo.m</code>
</div>

