# [DrawFormattedText2](DrawFormattedText2)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[nx, ny, textbounds, cache, wordbounds] = [DrawFormattedText2](DrawFormattedText2)(tstring, key-value pairs)  
or:  
[nx, ny, textbounds, cache, wordbounds] = [DrawFormattedText2](DrawFormattedText2)(cache, key-value pairs)  
  
When called with a string, the following key-value pairs are understood:  
win [, sx][, sy][, xalign][, yalign][, xlayout][, baseColor][, wrapat][, transform][, vSpacing][, righttoleft][, winRect][, resetStyle][, cacheOnly]  
Those enclosed in square braces are optional.  
  
When called with a cache struct, the following optional key-value pair  
arguments are accepted:  
[, win][, sx][, sy][, xalign][, yalign][, transform][, winRect][, cacheOnly]  
  
example call:  
[DrawFormattedText2](DrawFormattedText2)('test text', 'win',window\_pointer,'baseColor',[255 0 0])  
  
Draws a string of text 'tstring' into Psychtoolbox window 'win'. Allows  
some formatting and precise positioning. Only works with the FTGL-based  
text plugin (see help [DrawTextPlugin)](DrawTextPlugin)), activate it with  
[Screen](Screen)('[Preference](Preference)','TextRenderer', 1);  
This function is \_not\_ made to be fast. Test carefully if you want it to  
work within a screen refresh if you throw a lot of text at it.  
  
The text string 'tstring' may contain newline characters '\n'.  
Whenever a newline character '\n' is encountered, a linefeed and  
carriage return is performed, breaking the text string into lines.  
  
The text may also contain the formatting tags listed below. Each tag  
changes the formatting of the text from that point onward. Tags do not  
need to be closed. At the exit of the function, the state of the font  
renderer (font, text size, etc) is reset to the state upon function entry  
or the state stored in the cache if drawing from cache.  
- <i\>:                toggles italicization  
- <b\>:                toggles bolding  
- <u\>:                toggles underlining  
- <color=colorFmt\>    switches to a new color  
- <font=name\>         switches to a new font  
- <size=number\>       switches to a new font size  
The <i\>, <b\> and <u\> tags toggle whether text is italicized, bolded or  
underlined and remain active (possibly until the end of the input string)  
until the same <i\>, <b\> or <u\> tag is encountered again.  
The <color\>, <font\> and <size\> tags can be provided empty (i.e., without  
argument), in which case they cause to revert back to the color, font or  
size active before the previous switch. Multiple of these in a row go  
back further in history (until start color, font, size is reached).  
To escape a tag, prepend it with a slash, e.g., /<color\>. If you want a  
slash right in front of a tag, escape it by making it a double /:  
//<color\>. No other slashes should be escaped.  
<color\>'s argument can have one of two formats, it can either be a  
hexadecimal string (HEX), or a comma-separated floating point array  
(FPN). If a HEX input is provided, it should encode colors using a 1, 2,  
6 or 8 hexadecimal digit string. If 1 or 2 digits are provided, this is  
interpreted as a grayscale value. 6 hexadecimal digits are interpreted as  
R, G and B values (2 digits each). 8 digits further includes an alpha  
value. Using the HEX values, color values range from 0 to 255. Example:  
<color=ff0000\> changes the text color to red (ff corresponds to 255). The  
FPN format consists of 1, 3 or 4 comma separated floating point color  
values (luminance, RGB, or RGBA) that can take on any value, but will be  
processed according to the current color settings for the window as  
indicated by [Screen](Screen)('ColorRange'). Typically, the values provided will  
range from 0.0--1.0 per component. Floating point values should include  
the decimal point to ensure that single element FPN values are parsed  
correctly. Examples: <color=1.,0.,0.\> and <color=.5\>. If a floating point  
value is specified but [Screen](Screen)('ColorRange') returns 255, indicating 8bit  
color values are used for the window, the floating point color values  
provided are automatically scaled and rounded to the 0-255 range. If the  
HEX format is used but [Screen](Screen)('ColorRange') returns 1.0, indicating  
floating point color values are used for the window, the uint8 color  
values are automatically converted to the 0.0-1.0 range.  
A size/font command before a newline can change the height of the line on  
which it occurs. So if you want to space two words 'test' and 'text'  
vertically by white space equivalent to an 80pts line, use:  
'test\n<size=80\>\n<size\>text'. There is an empty line between the two new  
lines, and the size=80 says that this line has height of 80pts in the  
selected font.  
  
'sx' and 'sy' provide a location on the screen with respect to which the  
textbox is positioned. 'sx' and 'sy' can be a pixel location provided as  
a number. Alternatively, 'sx' can also be 'left' (default), 'center', or  
'right' signifying the left side, horizontal middle, or right side of the  
window rect. 'sy' can also be 'top' (default), 'center', or 'bottom'  
signifying the top, vertical middle, or bottom of the window rect.   
  
'xalign' and 'yalign' are text strings indicating how the textbox should  
be aligned to the screen location provided in 'sx' and 'sy'. For  
'xalign', 'left' (default), signifies that the left of the text's  
bounding box is aligned to the screen location; 'center' that the  
bounding box is centered on this location; and 'right' that the right of  
the text's bounding box is aligned with this location. For 'yalign',  
'top' (default), signifies that the top of the text's bounding box is  
aligned to the screen location; 'center' that the bounding box is  
centered on this location; and 'bottom' that the bottom of the text's  
bounding box is aligned with this location.  
  
'xlayout' indicates how each line is positioned horizontally in the  
bounding box. If 'left' (default), all lines are aligned to the left of  
the text's bounding box; if 'center', all lines are centered in the  
bounding box; and if 'right', all lines are aligned to the right of the  
bounding box. Justification options are currently not supported.  
  
'baseColor' is the color in which the text will be drawn (until changed  
by a <color\> format call). This is also the color that will remain active  
after invocation of this function.  
  
'wrapat', if provided, will automatically break text strings longer than  
'wrapat' characters into newline separated strings of roughly 'wrapat'  
characters. This is done by calling the [WrapString](WrapString) function (See 'help  
WrapString'). 'wrapat' mode may not work reliably with non-ASCII text  
strings, e.g., UTF-8 encoded uint8 strings on all systems. It also does  
not necessarily lead to lines of roughly equal length, unless using a  
monospace font.  
  
'transform' allows transforming the text to be drawn as a whole. The  
'transform' input is a cell array of key-value parameters, indicating  
which transform to do in which order. The following transform are  
supported:  
'translate', [dx dy]: translates text by dx horizontally and dy  
                      vertically  
'flip', axis        : mirrors text horizontally if axis is 1, vertically  
                      if axis is 2, and along both axes if number is 3  
                      (which is equal to a 180 deg rotation)  
'scale', [sx sy]    : scale text horizontally by sx and vertically by sy.  
                      Set to 1 if you want no scaling.  
'rotate', angle     : Rotate text by angle (degrees). Note that for the  
                      PTB screen, a positive rotation is clockwise.  
example {'translate',[100 0],'rotate',45} first translates text by 100  
pixels, then rotates it by 45 degree clockwise. Note that the order of  
operations is important. The above is equal to  
{'rotate',45,'translate',100\*sqrt([2 2])/2}. Advanced note: for [OpenGL](OpenGL)  
transform are applied in the reverse order from how they're specified.  
That is not the case for this interface, transform are applied in the  
order specified.  
  
The optional argument 'vSpacing' sets the spacing between the lines.  
Default value is 1.  
  
The optional argument 'winRect' allows to specify a [left top right  
bottom] rectangle, in which the text should be placed etc. By default, the  
rectangle of the whole 'win'dow is used.  
  
'resetStyle'. If true, we reset the base text style to normal before  
interpreting formatting commands that are present in the input text  
string. If not (false), active text style at function entry is taken into  
account when processing style toggle tags  
  
'cache'. Upon invocation of the function, it provides an optional output  
'cache'. Providing this output back to [DrawFormattedText2](DrawFormattedText2) instead of the  
'tstring' input allows direct drawing of the exact same text without all  
the preprocessing having to be done again, potentially saving significant  
time (and simplifying the call syntax). In this mode, a subset of the  
below arguments can be used to, e.g., draw to a different window or  
reposition the text. This cache can be generated without any actual  
drawing being done by setting the 'cacheOnly' argument to true. The cache  
is an implementation detail and is subject to change at any time.  
When drawing from cache, the text can be repositioned with the 'sx',  
'sy', 'xalign', 'yalign' and 'winRect' inputs described above. If only  
'sx' and 'sy' are provided, these are taken to be offsets to move the  
bounding box of the cached text. 'sx' and 'sy' must be numerical in this  
case and cannot be empty. If 'xalign' and/or 'yalign' are provided,  
full-fledged parsing of 'sx', 'sy', 'xalign' and 'yalign' is done, same  
as during a normal call to [DrawFormattedText2](DrawFormattedText2). The bounding box is then  
repositioned according to these for inputs. The winRect argument is only  
used in this case. It is optional (defaulting to the whole windows), and  
works as described above, specifying the rect to which 'xalign' and  
'yalign' apply. The input option 'transform' can furthermore be set,  
which appends additional transformations to what is already in the cache.  
  
  
### Return variables:  
  
The function returns the new (nx, ny) position of the text drawing cursor  
and the bounding rectangle 'textbounds' of the drawn string. (nx,ny) can  
be used as new start position for connecting further text strings to the  
bottom of the drawn text string. Calculation of textbounds is  
approximative, so it may give wrong results with some text fonts and  
styles on some operating systems, depending on the various settings. The  
optional 'cache' output argument is discussed above.  
  
When rotating by angles that are not a multiple of 90 degrees, the  
bounding box may not be accurate (too large). The returned bounding box  
is the rect that tightly fits the rotated original bounding box, not the  
box that tightly fits the rotated ink of the letters.  
  
The optional return argument 'wordbounds', if assigned in the calling  
function, returns a n-by-4 matrix of per-word bounding boxes. Each row  
defines a [left,top,right,bottom] rectangle with the bounding box of a  
word in the text string, ie. row 1 = first word, row 2 = 2nd word, ...  
white-space characters delimit single words, as do style changes and line-  
feeds, and these delimiters are not taken into account for the bounding box,  
ie. they don't get their own bounding boxes. The white-space separating  
successive words is as defined by the function isspace(tstring), or by a  
change of text style, color, formatting, etc. Use of 'wordbounds' may cause  
a significant slow-down in text drawing, so only assign this return argument  
if you actually need it. A current limitation is that returned bounding boxes  
will be likely incorrect if you apply multiple transformations like 'scale'  
'rotate', 'translate' and 'flip' at once. A single transformation will work,  
but multiple ones will cause misplaced per word bounding boxes. If you want  
to get proper 'wordbounds' when drawing text from the 'cache' then you must  
assign 'wordbounds' already in the [DrawFormattedText2](DrawFormattedText2)() invocation which  
returns the 'cache', otherwise bounding boxes might be wrong.  
  
One difference in the return values from this function and  
[DrawFormattedText](DrawFormattedText) is that the new (nx, ny) position of the text drawing  
cursor output is the baseline of the text. So to use (nx,ny) as the new  
start position for connecting further text strings, you need to draw  
these strings with yPositionIsBaseline==true. Another difference is that  
the returned textbounds bounding box includes the height of an empty line  
at the end if the input string ended with a carriage return.  
[DrawFormattedText](DrawFormattedText) only moved (nx,ny) but did not include the empty line  
in the bounding box. The empty line is also taken into account when  
centering text  
  
  
### Further Notes:  
  
Please note that while positioning and bounding boxes are pixel accurate  
with the fonts tested during development, i cannot guarantee this is the  
case with all fonts you throw at it. Also note that this function is not  
made to be fast. It has a make draw from cache mode so that all  
preprocessing is done only once and stored in a cache from which the text  
can be drawn directly. Nonetheless, especially if you throw a lot of  
formatting at it, this function may still not be fast in this mode. Use  
with caution in timing critical paths (test and measure to know if its  
fast enough). That said, with reasonable inputs it should manage to draw  
text to screen well within the inter frame interval of most screens.  
  
The function employs clipping by default. Text lines that are detected as  
laying completely outside the 'win'dow or optional 'winRect' will not be  
drawn, but clipped away. This allows to draw multi-page text (multiple  
screen heights) without too much loss of drawing speed. If you find the  
clipping to interfere with text layout of exotic texts/fonts at exotic  
sizes and formatting, you can define the global variable...  
global ptb\_drawformattedtext2\_disableClipping;  
... and set it like this ...  
ptb\_drawformattedtext2\_disableClipping = 1;  
... to disable the clipping.  
  
Regardless of the clipping setting, the optional 3rd return parameter  
'textbounds' always covers the complete text.  
  
See [DrawFormattedText2Demo](DrawFormattedText2Demo) for a usage example.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/DrawFormattedText2.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/DrawFormattedText2.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/DrawFormattedText2.m</code>
</div>

