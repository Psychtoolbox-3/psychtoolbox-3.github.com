# [TextOffByOneBugTest](TextOffByOneBugTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[TextBug](TextBug)  
Demonstrates an off-by-one bug in [Screen](Screen)('Drawtext'). The rendered text  
is drawn +1 pixel to the right of where it should be. This leaves the  
leftmost pixel unused, and clips off the rightmost pixel of the string.  
The bug is demonstrated here by drawing a letter twice, first in green as  
part of a string that has a space added (so no clipping occurs) and is  
then overwritten in black, without the added space. A green right edge is  
apparent in many rendered characters, at least in the Sloan font whose  
characters have no built-in spacing. The program also finds the bounding  
box of each character. For Sloan, the top bound is always zero, which is  
correct, but the left bound is always 1, which should also be zero.  
  
Denis Pelli March 21, 2007  
denis.pelli@...  
The Sloan font may be downloaded from here:  
http://psych.nyu.edu/pelli/software.html  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/TextOffByOneBugTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/TextOffByOneBugTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/TextOffByOneBugTest.m</code>
</div>

