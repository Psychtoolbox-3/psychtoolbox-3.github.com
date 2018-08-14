# [Screen('WaitBlanking')](Screen-WaitBlanking) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Wait for specified number of monitor refresh intervals, stopping PTB's execution  
until then. Select waitFrames=1 (or omit it, since that's the default) to wait  
for the beginning of the next frame. "windowPtr" is the pointer to the onscreen  
window for which we should wait for. framesSinceLastWait contains the number of  
video refresh intervals from the last time [Screen](Screen)('WaitBlanking') or  
[Screen](Screen)('[Flip](Flip)') returned until return from this call to [WaitBlanking](WaitBlanking). Please note  
that this function is only provided to keep old code from OS-9 PTB running. Use  
the [Screen](Screen)('[Flip](Flip)') command for all new code as this allows for much higher  
accuracy and reliability of stimulus timing and enables a huge number of new and  
very useful features! COMPATIBILITY TO OS-9 PTB: If you absolutely need to run  
old code for the old [MacOS](MacOS)-9 or Windows Psychtoolbox, you can switch into a  
compatibility mode by adding the command [Screen](Screen)('[Preference](Preference)', 'EmulateOldPTB',  
1) at the very top of your script. This will restore Offscreen windows and  
[WaitBlanking](WaitBlanking) functionality, but at the same time disable most of the new  
features of the [OpenGL](OpenGL) Psychtoolbox. Please do not write new experiment code in  
the old style! Emulation mode is pretty new and may contain significant bugs, so  
use with great caution!  


###See also:
[OpenWindow](Screen-OpenWindow) Flip Screen('Preference', 'EmulateOldPTB', 1)
