# [PlayMoviesWithoutGapDemo1](PlayMoviesWithoutGapDemo1)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[MovieDemos](MovieDemos)

  
[PlayMoviesWithoutGapDemo1](PlayMoviesWithoutGapDemo1)(moviename)  
  
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
  
See also [PlayMoviesWithoutGapDemo2](PlayMoviesWithoutGapDemo2) for a more efficient / even more "gapless"  
solution that can be used if all movies fulfill the constraints mentioned in  
that demo.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MovieDemos/PlayMoviesWithoutGapDemo1.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MovieDemos/PlayMoviesWithoutGapDemo1.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MovieDemos/PlayMoviesWithoutGapDemo1.m</code>
</div>

