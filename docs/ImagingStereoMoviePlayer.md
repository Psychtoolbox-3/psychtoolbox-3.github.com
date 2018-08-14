# [ImagingStereoMoviePlayer](ImagingStereoMoviePlayer)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[ImagingStereoMoviePlayer](ImagingStereoMoviePlayer)(moviefile [,stereoMode=8] [,imaging=1] [,anaglyphmode=0] [,screenid=max])  
  
Minimalistic movie player for stereo movies. Reads movie from file  
'moviefile'. Left half of each movie video frame must contain left-eye  
image, whereas right half of each frame must contain right-eye image.  
  
'stereoMode' mode of presentation, defaults to mode 8 (Red-Blue  
Anaglyph). 'imaging' if set to 1, will use the Psychtoolbox imaging  
pipeline for stereo display -- allows to set gains for anaglyph stereo  
and other more advanced anaglyph algorithms.  
  
stereoMode 103 activates stereo display on a VR HMD.  
  
'anaglyphmode' when imaging is enabled, allows to select the type of  
anaglyph algorithm:  
  
0 = Standard anaglyphs.  
1 = Gray anaglyphs.  
2 = Half-color anaglyphs.  
3 = Optimized color anaglyphs.  
4 = Full color anaglyphs.  
  
See "help [SetAnaglyphStereoParameters](SetAnaglyphStereoParameters)" for further description and references.  
  
'screenid' [Screen](Screen) id of target display screen (on multi-display setups).  
By default, the screen with maximum id is used.  
  
The left image is centered on the screen, the right images position can  
be moved by moving the mouse cursor to align for inter-eye distance.  
  
Press any key to quit the player.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/ImagingStereoMoviePlayer.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/ImagingStereoMoviePlayer.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/ImagingStereoMoviePlayer.m</code>
</div>

