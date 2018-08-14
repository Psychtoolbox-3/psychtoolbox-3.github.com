# [WrapString](WrapString)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

wrappedString=[WrapString](WrapString)(string,[maxLineLength])  
  
Wraps text by changing spaces into linebreaks '\n', making each line as  
long as possible without exceeding maxLineLength (default 74  
characters). [WrapString](WrapString) does not break words, even if you have a word  
that exceeds maxLineLength. The returned "wrappedString" is identical to  
the supplied "string" except for the conversion of some spaces into  
linebreaks. Besides making the text look pretty, wrapping the text will  
make the printout narrow enough that it can be sent by email and  
received as sent, not made hard to read by mindless breaking of every  
line.  
  
Note that this schemes is based on counting characters, not pixels, so  
it will give a fairly even right margin only for monospaced fonts, not  
proportionally spaced fonts. The more general solution would be based on  
counting pixels, not characters, using either [Screen](Screen) 'TextWidth' or  
[TextBounds](TextBounds).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/WrapString.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/WrapString.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/WrapString.m</code>
</div>

