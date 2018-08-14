# [TextBoundsTest](TextBoundsTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[TextBoundsTest](TextBoundsTest)([string] [, font] [, textSize] [, rotAngle])  
  
Test [Screen](Screen)('TextBounds') as a fast way of determining the bounding  
rectangle (aka bounding box) of a string of text, as well as the very  
precise but slow [TextBounds](TextBounds).m function.  
  
[Screen](Screen)('TextBounds') uses information from the operating system about the  
bounding polygons of a string of text to compute the bounding box. This  
is fast, but it relies on the typesetting algorithms of the OS and the  
information encoded in a font definition file playing well with each  
other. Usually that's the case, but there are a few special fonts which  
either don't encode their own boundaries correctly, or which are typeset  
in an unusual way that the OS facilities can't handle correctly. In such  
cases, textbounds will be way to big or too small and text may appear cut  
off.  
  
The [TextBounds](TextBounds)() function implemented in [TextBounds](TextBounds).m uses a different  
approach: It draws the text string into a provided window - usually an  
offscreen window which is so big that it can easily accomodate the text  
string in question, ie., it is way too big for the string. Then it reads  
back the image of that string and computes the exact bounding box of the  
non-background pixels. This method is obviously independent of OS  
facilities and (faulty) information in the font files - thereby highly  
robust and accurate. However the approach is very slow, so you should  
only use this method if you really need it.  
  
This test script both tests functioning of both methods and provides a  
code example of how to use the information returned by both methods to  
either frame drawn text, or to actually draw unusual difficult text by  
first predrawing it into an offscreen window of sufficient size, then  
blitting the really "meaningful" portions of that offscreen window into  
the real image window.  
  
Optional parameters: (All have meaningful defaults)  
'string' The text string to draw. Default: "Wordy"  
'font' Name of the font definition file. Default: "Chicago"  
'textSize' Size of text font. Default: 64 pts.  
'rotAngle' Orientation of test-blitted text. Default: 45 degrees.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/TextBoundsTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/TextBoundsTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/TextBoundsTest.m</code>
</div>

