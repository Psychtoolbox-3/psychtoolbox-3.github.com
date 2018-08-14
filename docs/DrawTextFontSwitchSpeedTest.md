# [DrawTextFontSwitchSpeedTest](DrawTextFontSwitchSpeedTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[DrawTextFontSwitchSpeedTest](DrawTextFontSwitchSpeedTest) - Test font settings switching speed.  
  
This is a benchmark of the speed with which [Screen](Screen)('DrawText') et al.  
can handle switching between different font settings between text  
drawing. Specifically it tests switching between different text sizes, text  
styles and font families. It also performs non-switched drawing to establish  
a baseline.  
  
After running for a thousand repetitions for each conditon, it prints a  
summary of drawing speed and then exits.  
  
### Background:  
  
In an ideal world, changing text settings should not slow down text drawing.  
In the real world, each time you change a text setting, [Screen](Screen)() needs to  
recompute various things, e.g., it needs to load new font data from the  
filesystem, rasterize glyphs into little images, convert them into [OpenGL](OpenGL)  
textures and upload them into the graphics card. This takes time and slows  
down text drawing after each change of settings.  
  
The Linux text renderer can cache the precomputed data for multiple different  
sets of text settings. This means that if you alternate repeatedly between a limited  
number of different text settings, e.g., drawing text strings of different font, size or  
style within one stimulus frame, then this will be only slow on the first stimulus frame.  
Linux ptb will remember the computed font data in a cache and recycle it in successive  
repetitions of those text settings. Therefore any repetition of a previously used text  
setting is "free" and fast. The number of cacheable settings is limited, as it consumes  
memory, currently to about 40 different settings. If you exceed that number, [Screen](Screen)  
will expunge the least used settings and be intelligent about what to recycle and what  
not. If you use non-repetitive settings then of course no caching in the world will help  
you. If no caching can be used - or at first use of a setting - subsequent text drawing will  
be about 10 - 15 times slower.  
  
On other operating systems, nothing will be cached or recycled, resulting in generally  
much slower text drawing speeds, even with constant text settings.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/DrawTextFontSwitchSpeedTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/DrawTextFontSwitchSpeedTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/DrawTextFontSwitchSpeedTest.m</code>
</div>

