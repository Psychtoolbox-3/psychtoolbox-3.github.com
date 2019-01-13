# [Screen('TextStyle')](Screen-TextStyle) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

oldStyle=Screen('TextStyle', windowPtr [,style]);

Get/set the font style for future text draws in this window. Useful values for  
style follow; they may be OR'd. On different operating systems and text  
renderers only a subset of these flags is honored. All settings are accepted on  
all systems, but some of them are silently ignored on some systems.  
0=normal,1=bold,2=italic,4=underline,8=outline,32=condense,64=extend.  
Normal, bold, and italic styles are supported on all systems and renderers.  
Underline is supported on OSX and Windows. Outline is supported on Linux.  
Condense and Extend are supported on Linux and OSX.  
You can assign a default font style for new windows via a call to  
[Screen](Screen)('[Preference](Preference)', 'DefaultFontStyle'). The initial default font style is  
operating system dependent.  
Not all fonts support all style settings. Unsupported settings for the currently  
selected font will be silently ignored.  


###See also:

