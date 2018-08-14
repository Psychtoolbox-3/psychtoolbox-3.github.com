# [DotDemo](DotDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

  
dot motion demo using SCREEN('DrawDots') subfunction  
  
Usage: [DotDemo](DotDemo)([showSprites = 0][, waitframes = 1]);  
  
The optional parameter 'showSprites' when set to 1, will draw little  
smiley textures instead of dots, demonstrating sprite-drawing. A zero  
setting, or omitting the setting, will draw dots. A value of 2 will draw  
filled rectangles via textures instead, (ab-)using texture drawing and  
filtering to allow subpixel positioning of drawn rectangles on the  
screen. We slow down the animation for non-zero 'showSprites' so you can  
appreciate the anti-aliased smooth subpixel movement better.  
  
'waitframes' Number of video refresh intervals to show each image before  
updating the dot field. Defaults to 1 if omitted.  
  
You can exit the demo by any keypress or mouse button press. It will also  
exit by itself after 1000 redraws.  
  
The top of the demo code contains tons of parameters to tweak and  
manipulate if you want.  
  
  
Note: Some versions of [MacOS](MacOS)/X have defective dot drawing due to an  
operating system bug. If you happen to have such a system (e.g., OS/X  
10.6.3 with [NVidia](NVidia) Geforce-7xxx hardware) then read "help [ScreenDrawDots](ScreenDrawDots)"  
for a workaround.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/DotDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/DotDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/DotDemo.m</code>
</div>

