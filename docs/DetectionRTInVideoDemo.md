# [DetectionRTInVideoDemo](DetectionRTInVideoDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[MovieDemos](MovieDemos)

  
[DetectionRTInVideoDemo](DetectionRTInVideoDemo)(moviename, timeOfEvent, trials)  
  
A demo implementation of how to collect reaction time for detection of a  
specific time-locked event in a movie file.  
  
Parameters:  
moviename - Filename of moviefile to use. If none is provided, then the  
simple [DualDiscs](DualDiscs) collision movie is used which is part of PTB.  
  
timeOfEvent - Time (in seconds) when the timelocked event happens which  
should be detected by the subject. Default is time of contact of the  
[DualDiscs](DualDiscs) collision.  
  
trials - Number of trials to run. Defaults to 10 or ESC key press.  
  
How the demo works: Read the source code - its well documented ;-)  
This demo demonstrates the optimal way if you have movies with sound  
(that needs to be played in sync with the video) or long movies that  
don't fit into memory or that you don't want to load into memory.  
  
It uses automatic synchronized audio-video playback. The central  
while-loop checks for arrival of new frames for display and displays them  
when their time has come. It also registers subjects keypress responses  
and does all the bookkeeping and sanity checking.  
  
An alternative approach would be to preload the whole movie into textures:  
The whole movie gets read into PTB textures before start of trial. Then  
you show the textures in quick succession like in [MovieDemo](MovieDemo). The  
advantage of that approach is exact control over display timing and  
display order: You can show frames in any order you like at any rate you  
like (and that your hardware likes). Disadvantage would be: Longer trial  
setup time for loading the whole movie, higher memory consumption (keep  
all n frames in memory instead of only the current one) and the inability  
to play sound in sync with video.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MovieDemos/DetectionRTInVideoDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MovieDemos/DetectionRTInVideoDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MovieDemos/DetectionRTInVideoDemo.m</code>
</div>

