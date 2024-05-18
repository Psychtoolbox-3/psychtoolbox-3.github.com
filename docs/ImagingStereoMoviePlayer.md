# [ImagingStereoMoviePlayer](ImagingStereoMoviePlayer)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[ImagingStereoMoviePlayer](ImagingStereoMoviePlayer)(moviefile [, stereoMode=8][, imaging=1][, anaglyphmode=0][, screenid=max][, hdr=0][, topBottom=0])  
  
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
  
If the optional flag 'hdr' is specified as non-zero, then the demo  
expects the onscreen window to display on a HDR-10 capable display device  
and system, and tries to switch to HDR mode. If the operating system+gpu  
driver+gpu+display combo does not support HDR, the demo will abort with  
an error. Otherwise it will expect the movies to be HDR-10 encoded and  
try to display them appropriately. A flag of 1 does just that. A flag of 2 will  
manually force the assumed EOTF of movies to be of type PQ, iow. assume the movie  
is a HDR-10 movie in typical Perceptual Quantizer encoding. This is useful if you  
want to play back HDR content on a system with a [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) version older than  
1.18.0 installed, where [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) is not fully HDR capable, but this hack may  
get you limping along. Another restriction would be lack of returned HDR metadata,  
so if your HDR display expects that, you will not get the best possible quality.  
Upgrading to [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) 1.18 or later is advised for HDR playback.  
A 'stereoMode' of 4 or 5 will use an alternative HDR display method only available on  
Linux/X11 for dual-display HDR playback. This is currently not supported on other  
operating systems, where you only have single-display stereo for HDR playback.  
  
'topBottom' If this optional flag is set to 1, then top-bottom encoding in the  
movie is assumed and handled accordignly, otherwise left-right encoding is assumed.  
  
  
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

