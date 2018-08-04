# [PlayMoviesWithoutGapDemo2](PlayMoviesWithoutGapDemo2)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[MovieDemos](MovieDemos)

[PlayMoviesWithoutGapDemo2](PlayMoviesWithoutGapDemo2)(moviename)  
  
This demo accepts a pattern for a valid moviename, e.g.,  
moviename='\*.mpg', then it plays all movies in the current working  
directory whose names match the provided pattern, e.g., the '\*.mpg'  
pattern would play all MPEG files in the current directory.  
  
Pressing ESC ends the demo.  
  
Movies are played one after each other. We try to minimize perceptible  
gaps between end of movie i and start of movie i+1 by asynchronous  
loading: While movie i is played back, we ask Psychtoolbox to load the  
next movie i+1 in the background, so startup time for movie i+1 will be  
minimized.  
  
This method uses only one 'movie' object for successive, gapless playback  
of many movie files. The advantage is simplicity in use and maximum  
quality in the sense that movies should play back-to-back without any  
significant delays between them. The downside is loss in flexibility.  
This method only works if all movies have exactly the same image size,  
color depth and format, aspect ratio and playback framerate. They may  
only differ in filename, content and duration. Any other difference will  
cause malfunctions, even hard crashes of Matlab or Octave!  
  
If you need a method that is more flexible and can handle movies of  
different format, use the method in [PlayMoviesWithoutGapDemo1](PlayMoviesWithoutGapDemo1). That  
method can handle arbitrary movies. The downside is a higher likelyhood  
of small gaps between movies.  
  
History: 14.03.2012  mk  Wrote it, derived from [PlayMoviesWithoutGapDemo1](PlayMoviesWithoutGapDemo1).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MovieDemos/PlayMoviesWithoutGapDemo2.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MovieDemos/PlayMoviesWithoutGapDemo2.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MovieDemos/PlayMoviesWithoutGapDemo2.m</code>
</div>

