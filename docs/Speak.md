# [Speak](Speak)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

Use speech output to speak a given text.  
  
### Usage:  
  
[ ret ] = Speak(text [, voice][, rate][, volume][, pitch][, language]);  
  
The function returns an optional 'ret'urn code 0 on success, non-zero  
on failure to speak the requested text.  
  
'text' must be a text to speak, either a text string or a cell array  
of text strings to speak separately, cell by cell.  
  
The optional 'voice' parameter allows to select among different system  
voices. It is supported on Linux and Mac OS/X.  
  
The names of the available voices differ across operating systems.  
  
Linux supports, e.g., male1,  male2,  male3,  female1,  female2,  
female3, child\_male, child\_female.  
  
OS/X: Type "!say -v ?" in Matlab to get a list of supported voices.  
  
The optional 'rate' parameter controls speed of speaking on OS/X and  
Linux. On OS/X it defines the number of words per minute, on Linux a  
value between -100 and +100 defines slower or faster speed.  
  
The optional 'volume' parameter allows control of loudness on Linux:  
Value range is -100 to + 100.  
  
The optional 'pitch' parameter allows control of pitch on Linux:  
Value range is -100 to + 100.  
  
The optional 'language' parameter allows control of the output language  
on Linux. E.g., 'de' would output in german language, 'en' english  
language. The text string must be a valid ISO language code string.  
  
Note: Speak on MS-Windows requires the .NET framework to be installed.  
Note: Speak on Linux requires the spd-say command to be installed. This  
is the case by default, e.g., at least on Ubuntu Linux 12.04 and later.  
  
Examples:  
Say "Hello darling" with standard system voice:  
Speak('Hello darling');  
  
Say same text with voice named "Albert":  
Speak('Hello darling', 'Albert');  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/Speak.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/Speak.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/Speak.m</code>
</div>

