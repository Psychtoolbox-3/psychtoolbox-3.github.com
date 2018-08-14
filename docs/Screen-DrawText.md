# [Screen('DrawText')](Screen-DrawText) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Draw text. "text" may include Unicode characters (e.g. Chinese).  
A standard Matlab/Octave char()acter text string is interpreted according to  
[Screen](Screen)'s current character encoding setting. By default this is the "system  
default locale", as selected in the language settings of your user account. You  
can change the encoding anytime via a call to [Screen](Screen)('[Preference](Preference)',  
'TextEncodingLocale', newencoding); E.g., for UTF-8 multibyte character encoding  
you'd call [Screen](Screen)('[Preference](Preference)','TextEncodingLocale','UTF-8');  
If you have a non-ASCII text string and want to make sure that Matlab or Octave  
doesn't meddle with your string, convert it into a uint8() datatype before  
passing to this function.  
If you want to pass a string which contains unicode characters directly, convert  
the text to a double matrix, e.g., mytext = double(myunicodetext); then pass the  
double matrix to this function. [Screen](Screen) will interpret all double numbers  
directly as unicode code points.  
Unicode text drawing is supported on all operating systems if you select the  
default high quality text renderer. Of course you also have to select a text  
font which contains the unicode character sets you want to draw - not all fonts  
contain all unicode characters.  
The following optional parameters allow to control location and color of the  
drawn text:  
"x" "y" defines the text pen start location. Default is the location of the pen  
from previous draw text commands, or (0,0) at startup. "color" is the CLUT index  
(scalar or [r g b] triplet or [r g b a] quadruple) for drawing the text; startup  
default produces black.  
"backgroundColor" is the color of the background area behind the text. By  
default, text is drawn transparent in front of whatever image content is stored  
in the window. You need to set an explicit backgroundColor and possibly enable  
user defined alpha-blending with [Screen](Screen)('[Preference](Preference)', 'TextAlphaBlending', 1);  
and [Screen](Screen)('Blendfunction', ...) to make use of text background drawing.  
Appearance of the background + text may be different accross different operating  
systems and text renderers, or it may not be supported at all, so this is not a  
feature to rely on.  
"yPositionIsBaseline" If specified, will override the global preference setting  
for text positioning: It defaults to off. If it is set to 1, then the "y" pen  
start location defines the base line of drawn text, otherwise it defines the top  
of the drawn text. Old PTB's had a behaviour equivalent to setting 1,  
unfortunately this behaviour wasn't replicated in early versions of  
Psychtoolbox-3, so now we stick to the new behaviour by default.  
"swapTextDirection" If specified and set to 1, then the direction of the text is  
swapped from the default left-to-right to the swapped right-to-left direction,  
e.g., to handle scripts with right-to-left writing order like hebrew.  
"newX, newY" optionally return the final pen location.  
"textHeight" optionally return height of current text string. May return zero if  
this is not supported by the current text renderer.  
Btw.: [Screen](Screen)('[Preference](Preference)', ...); provides a couple of interesting text  
preference settings that affect text drawing, e.g., setting alpha blending and  
anti-aliasing modes.  
Selectable text renderers: The [Screen](Screen)('[Preference](Preference)', 'TextRenderer', Type);  
command allows to select among different text rendering engines with different  
properties:  
Type 0 is the legacy OS specific text renderer: On Linux this is implemented as  
a fast, but low quality [OpenGL](OpenGL) display list renderer without any support for  
unicode or text anti-aliasing. On MS-Windows, this is currently a GDI based  
renderer. On OSX this currently selects Apples [CoreText](CoreText) text renderer, which is  
slow but does support anti-aliasing, unicode and other features. Normally you  
really don't want to use the type 0 legacy renderer. It is provided for  
backwards compatibility to old experiment scripts and may need to get removed  
completely in future versions of Psychtoolbox due to circumstances out of our  
control.  
Type 1 is the high quality renderer: It supports unicode, anti-aliasing, and  
many other interesting features. This is a renderer loaded from an external  
plugin, and based on FTGL for fast high quality text drawing with [OpenGL](OpenGL).  
This function doesn't provide support for text layout. Use the higher level  
[DrawFormattedText](DrawFormattedText)() function if you need basic support for text layout, e.g,  
centered text output, line wrapping etc.  
  


###See also:
[TextBounds](Screen-TextBounds) [TextSize](Screen-TextSize) [TextFont](Screen-TextFont) [TextStyle](Screen-TextStyle) [TextColor](Screen-TextColor) [TextBackgroundColor](Screen-TextBackgroundColor) Preference
