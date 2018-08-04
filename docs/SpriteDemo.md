# [SpriteDemo](SpriteDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[SpriteDemo](SpriteDemo)  
  
Animates a sprite across the screen.  The image  
follows the mouse, like a huge cursor.  
  
There are many ways to create animations.  The simplest is to show a  
movie, computing all the frames in advance, as in [MovieDemo](MovieDemo).  Sprites may  
be a better approach when you want to show a relatively small object  
moving unpredictably.  Here we generate one offscreen window holding the  
sprite image and copy it to the screen for each frame of the animation,  
specifying the screen location by using the destination rect argument of  
[Screen](Screen) 'CopyWindow'.  
  
See also [MovieDemo](MovieDemo).  
  
Thanks to tj <thomasjerde@hotmail.com\> for asking how.   
web http://groups.yahoo.com/group/psychtoolbox/message/1101 ;  
  
6/20/02 awi  Wrote it as [TargetDemo](TargetDemo).    
6/20/02 dgp  Cosmetic.  Renamed [SpriteDemo](SpriteDemo).  
8/25/06 rhh  Added noise to the sprite.  Expanded comments.  
10/14/06 dhb Save and restore altered prefs, more extensive comments for them  
09/20/09 mk  Improve screenNumber selection as per suggestion of Peter April.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/SpriteDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/SpriteDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/SpriteDemo.m</code>
</div>

