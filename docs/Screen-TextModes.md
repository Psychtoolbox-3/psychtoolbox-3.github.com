# [Screen('TextModes')](Screen-TextModes) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

textModes = Screen('TextModes');

Return a cell array of strings naming allowable text modes for  
[Screen](Screen)('TextMode').  
Please note that none of these modes are supported in the current Psychtoolbox,  
except on OSX with its default text renderer 1 aka the Apple [CoreText](CoreText) renderer,  
so whatever 'TextMode' you set will be silently ignored and have no effect.   


###See also:
[TextMode](Screen-TextMode)
