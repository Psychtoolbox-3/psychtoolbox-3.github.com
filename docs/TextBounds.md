# [TextBounds](TextBounds)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

bounds=[TextBounds](TextBounds)(window, string [, yPositionIsBaseline=0][, centerTheText=0])  
  
Returns the smallest enclosing rect for the drawn text, relative to the  
current location. This bound is based on the actual pixels drawn, so it  
incorporates effects of text smoothing, etc. "text" may be a cell array  
or matrix of 1 or more strings. The strings are drawn one on top of  
another, at the same initial position, before the bounds are calculated.  
This returns the smallest box that will contain all the strings. The  
prior contents of the scratch window are lost. Usually it should be an  
offscreen window, so the user won't see it. The scratch window should be  
at least twice as wide and high as the text, to cope with uncertainties  
about text direction (e.g. Hebrew) and some unusual characters that  
extend greatly to the left of their nominal starting point. If you only  
know your nominal text size and number of characters, you might do this  
to create your scratch window:  
  
Get the bounding box.  
textSize=48;  
string='Good morning.';  
yPositionIsBaseline=1; % 0 or 1  
w=[Screen](Screen)('OpenWindow',0,255);  
woff=[Screen](Screen)('OpenOffscreenWindow',w,[],[0 0 2\*textSize\*length(string) 2\*textSize]);  
[Screen](Screen)(woff,'TextFont','Arial');  
[Screen](Screen)(woff,'TextSize',textSize);  
t=[GetSecs](GetSecs);  
bounds=[TextBounds](TextBounds)(woff,string,yPositionIsBaseline)  
fprintf('TextBounds took %.3f seconds.\n',[GetSecs](GetSecs)-t);  
[Screen](Screen)('[Close](Close)',woff);  
  
Show that it's correct by using the bounding box to frame the text.  
x0=100;  
y0=100;  
[Screen](Screen)(w,'TextFont','Arial');  
[Screen](Screen)(w,'TextSize',textSize);  
[Screen](Screen)('DrawText',w,string,x0,y0,0,255,yPositionIsBaseline);  
[Screen](Screen)('FrameRect',w,0,[InsetRect](InsetRect)[(OffsetRect]((OffsetRect)(bounds,x0,y0),-1,-1));  
[Screen](Screen)('[Flip](Flip)',w);  
Speak('Click to quit');  
[GetClicks](GetClicks);  
[Screen](Screen)('[Close](Close)',w);  
  
The suggested window size in that call is generously large because there  
aren't any guarantees from the font makers about how big the text might  
be for a specified point size. Set your window's font, size, and  
(perhaps) style before calling [TextBounds](TextBounds).  
  
Be warned that [TextBounds](TextBounds) and [TextCenteredBounds](TextCenteredBounds) are slow (taking many  
seconds) if the window is large. They use the whole window, so if the  
window is 1024x1024 they process a million pixels. The two slowest calls  
are [Screen](Screen) 'GetImage' and FIND. Their processing time is proportional to  
the number of pixels in the window. So keep your window small.  
  
Also see [Screen](Screen) 'TextBounds'.  
Also see [TextCenteredBounds](TextCenteredBounds).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/TextBounds.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/TextBounds.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/TextBounds.m</code>
</div>

