# [GetEchoNumber](GetEchoNumber)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

number = [GetEchoNumber](GetEchoNumber)(window, msg, x, y [, textColor][, bgColor][, deviceIndex][, untilTime=inf][, [KbCheck](KbCheck) args...])  
  
Get a number typed at the keyboard. Entry is terminated by <return\> or  
<enter\>. Typed characters are displayed on the screen. Useful for i/o in  
a [Screen](Screen) window. Equivalent to "number = str2num[(GetEchoString]((GetEchoString)(...))".  
  
Returns the empty matrix if no valid number is entered within the timeout  
period defined by the optional 'untilTime' deadline. Returns a column vector  
with multiple numbers if more than one number is entered, e.g., typing  
multiple numbers separated by a space or a comma.  
  
Typed characters are displayed in the window. The delete or backspace key  
is handled correctly, ie., it erases the last typed number.  
  
'window' = Window to draw to. 'msg' = A message string displayed to  
prompt for input. 'x', 'y' = Start position of message prompt.  
'textColor' = Color to use for drawing the text. 'bgColor' = Background  
color for text. By default, the background is transparent. If a non-empty  
'bgColor' is specified it will be used. The current alpha blending  
setting will affect the appearance of the text if 'bgColor' is specified!  
  
Please note that if 'bgColor' is not specified, this means mistyped numbers  
can't be visually deleted/undone by use of the backspace key.  
  
This function uses [GetKbChar](GetKbChar)() and thereby [KbCheck](KbCheck)() to get keyboard input.  
The optional  'deviceIndex' argument optionally allows to select the  
deviceIndex of the keyboard to use, and 'untilTime' allows to specify a  
response deadline. If the user doesn't press ENTER until 'untilTime', the  
function will time out and return with a empty 'number' as result. Further  
optional arguments will be passed on to the function [GetKbChar](GetKbChar)().  
  
See also: [GetNumber](GetNumber), [GetString](GetString), [GetEchoString](GetEchoString), [GetKbChar](GetKbChar)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/GetEchoNumber.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/GetEchoNumber.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/GetEchoNumber.m</code>
</div>

