# [Screen('TextFont')](Screen-TextFont) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Get/Set the font for future text draws in this window.  
You can ask what the current font is, or specify the desired font by number or  
by name (e.g. 'Helvetica'). Font numbers are not consistent from Mac to Mac, and  
they aren't supported but silently ignored on MS-Windows and Linux, so use font  
names for reliability and portability. Font numbers are mostly available for  
backward compatibility to old OS-9 Psychtoolbox versions.  
The font name can be a string of at most 255 characters length, e.g.  
'Helvetica', or a list containing one string of at most 255 characters, e.g.  
{'Helvetica'}. The default font depends on the operating system and is selected  
for good readability. You can query and change it via a call to  
[Screen](Screen)('[Preference](Preference)', 'DefaultFontName').  
It's ok to request a non-existent font; this will have no effect. If you care,  
call [TextFont](TextFont) again to find out whether you got the font you requested. See  
[FontDemo](FontDemo).  
On OSX there are some exotic fonts which can only be selected if you specify  
them by either their font number, or by simultaneously selecting their exact  
font family name and text style. To support those snow flakes you can specify  
the optional 'textStyle' argument together with the font name.  
On Linux - and usually OSX - you can either provide a font name - PTB will  
select the closest matching available font for that name, size and style  
requirements - or you can start the fontName with a dash '-' followed by a full  
[FontConfig](FontConfig) font specifier string which encodes all kinds of properties. The  
'fc-list' command under Linux allows you to query all available fonts.  
Depending on the selected text renderer, Linux can be picky about the supplied  
fonts - if you request a non-existent font with the legacy text renderer, the  
[DrawText](DrawText) command will fail with an error message. However, with the default FTGL  
text renderer on Linux, Linux will be lenient in its font selection. If you call  
[Screen](Screen)('TextFont') after you've drawn some text, the command will return the  
font family name of the true selected font.   


###See also:

