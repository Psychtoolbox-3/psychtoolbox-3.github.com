# [GetEchoString](GetEchoString)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[string,terminatorChar] = [GetEchoString](GetEchoString)(window,msg,x,y,[textColor],[bgColor],[useKbCheck=0],[deviceIndex],[untilTime=inf],[[KbCheck](KbCheck) args...]);  
  
Get a string typed at the keyboard. Entry is terminated by <return\> or  
<enter\>.  
  
Typed characters are displayed in the window. The delete or backspace key  
is handled correctly, ie., it erases the last typed character. Useful for  
i/o in a [Screen](Screen) window.  
  
'window' = Window to draw to. 'msg' = A message string displayed to  
prompt for input. 'x', 'y' = Start position of message prompt.  
'textColor' = Color to use for drawing the text. 'bgColor' = Background  
color for text. By default, the background is transparent. If a non-empty  
'bgColor' is specified it will be used. The current alpha blending  
setting will affect the appearance of the text if 'bgColor' is specified!  
Please note that if 'bgColor' is not specified, this means mistyped text  
can't be visually deleted/undone by use of the backspace key.  
  
If the optional flag 'useKbCheck' is set to 1 then [KbCheck](KbCheck) is used - with  
potential optional additional 'KbCheck args...' for getting the string  
from the keyboard. Otherwise [GetChar](GetChar) is used. 'useKbCheck' == 1 is  
restricted to standard alpha-numeric keys (characters, letters and a few  
special symbols). It can't handle all possible characters and doesn't  
work with non-US keyboard mappings. Its advantage is that it works  
reliably on configurations where [GetChar](GetChar) may fail, e.g., on MS-Vista and  
Windows-7.  
  
If 'useKbCheck' == 1, then 'deviceIndex' optionally allows to select the  
deviceIndex of the keyboard to use, and 'untilTime' allows to specify a  
response deadline. If the user doesn't press ENTER until 'untilTime', the  
function will time out and return with a empty 'string' as result. Further  
optional arguments will be passed on to the function [GetKbChar](GetKbChar)().  
  
See also: [GetNumber](GetNumber), [GetString](GetString), [GetEchoNumber](GetEchoNumber), [GetKbChar](GetKbChar)  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/GetEchoString.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/GetEchoString.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/GetEchoString.m</code>
</div>

