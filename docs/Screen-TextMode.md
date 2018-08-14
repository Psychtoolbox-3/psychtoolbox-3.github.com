# [Screen('TextMode')](Screen-TextMode) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Set or get the text mode for the specified window. This function currently  
hasn't any effect whatsoever on systems other than OSX with its default  
textrenderer 1. If you use it, your code will become non-portable and possibly  
not future proof if we would decide to remove the Apple [CoreText](CoreText) renderer from  
OSX. On unsupported systems any setting made here will be silently ignored.  


###See also:
[TextModes](Screen-TextModes)
