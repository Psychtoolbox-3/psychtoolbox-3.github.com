# [VideoCaptureLatencyTest](VideoCaptureLatencyTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[VideoCaptureLatencyTest](VideoCaptureLatencyTest)  
  
This routine tests the latency of Videocapture for  
a given Camera -\> Computer -\> PTB -\> gfx-card -\> display combo.  
  
### Working principle and usage:  
  
1. Point camera to monitor so that cameras field of view captures monitor  
display area.  
  
2. Calibration: First a black screen is shown to the cam and captured to  
find the average intensity of an image of a black display.  
Then (over ten trials), the screen turns white and the script measures  
the time delay between onset of white screen and arrival of a captured  
image with at least 25% more intensity than the 'black'-image -- our  
white image. This procedure is repeated 10 times and latencies averaged.  
  
-\> Rough estimate of delay from scene change to arrival of frame.  
-\> You have to add the display onset delay if captured image should be  
shown to subject for video feedback loops.  
  
### Parameters:  
  
texfetch == 0 Measure only capture latency. 1 == Measure texture fetch  
latency as well. 2 == Measure drawing and onset latency as well.  
  
History:  
2/9/06 mk Written.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/VideoCaptureLatencyTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/VideoCaptureLatencyTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/VideoCaptureLatencyTest.m</code>
</div>

