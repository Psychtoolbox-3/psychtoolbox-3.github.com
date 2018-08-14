# [DrawingSpeedTest](DrawingSpeedTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[DrawingSpeedTest](DrawingSpeedTest)([n=800][,primitivetype=0][,mode=0][,gpumeasure=0])  
  
Tests batch-drawing performance of some [Screen](Screen) functions. Batch drawing  
is a way to submit multiple primitives, e.g., Filled Rects, at once. This  
way the Matlab call overhead and some internal setup overhead is saved  
and drawing should be significantly faster than when issuing single  
drawing commands in a loop.  
  
This currently only tests filled rects and framed rects as well as filled  
ovals. It also provides a way to test drawing by texture mapping.  
Dots and Lines are nicely demonstrated by [DotDemo](DotDemo) and [LinesDemo](LinesDemo).  
  
The optional parameter n allows to specifiy the number of primitives to  
draw each frame, default is 800. The test loop will draw 1000 identical  
frames and measure the time needed.  
  
'primitivetype' type of primitive: 0 = filled rects, 1 = framed rects, 2  
= filled ovals, 3 = framed ovals.  
  
'mode' type of drawing: 0 = One by one submission (slowest), 1 = batch  
submission, 2 = texture mapping for drawing, 3 = texture mapping with  
batch submission of textures.  
  
'gpumeasure' measurement type: 0 = Only on cpu. 1 = Measure exact  
execution time of drawing commands on GPU's that support this feature.  
Plot result at end of run.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/DrawingSpeedTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/DrawingSpeedTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/DrawingSpeedTest.m</code>
</div>

