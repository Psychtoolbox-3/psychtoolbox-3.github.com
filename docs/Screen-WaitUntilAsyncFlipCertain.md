# [Screen('WaitUntilAsyncFlipCertain')](Screen-WaitUntilAsyncFlipCertain) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Wait until it is certain that a previously initiated  
[Screen](Screen)('AsyncFlipBegin',...); operation for onscreen window 'windowPtr' will  
happen at next vertical retrace or has happened already, then return timestamps  
of when flip operation has happened or when the flip operation will happen.  
This function only works on Linux and [MacOS](MacOS)/X and only with recent AMD/ATI  
hardware of the Radeon X1000/HD2000/... series or later (or the equivalent  
[FireGL](FireGL) cards). On [MacOS](MacOS)/X, the [PsychtoolboxKernelDriver](PsychtoolboxKernelDriver) needs to be loaded for  
this to work (see help [PsychtoolboxKernelDriver)](PsychtoolboxKernelDriver)).  
The method tries to "read the mind" of your graphics card to find out if the  
card will swap the display buffers at the next vertical retrace to interrogate  
if the swap is certain, ie., not possibly delayed by graphics card overload,  
other overload conditions or system timing jitter/delays.  
Ideally it will allow your script to know when stimulus onset will happen a few  
milliseconds before stimulus onset. This allows, e.g., to initiate some other  
operations that need to be tightly and reliably synchronized to stimulus onset  
and that have some small startup latency, so they need some headstart. Examples  
would be sound output or output of some slow trigger signal which takes multiple  
milliseconds to take action.  
This feature only works in fullscreen mode and is considered experimental - It  
may or may not work reliably on your setup. Good luck!  
Returns a high-precision estimate of the system time (in seconds) when the  
actual flip will- or has happened in the return argument 'VBLTimestamp'. An  
estimate of Stimulus-onset time is returned in 'StimulusOnsetTime'.  
'swapCertainTime' is the system time when certainty of bufferswap was detected.   


###See also:
'AsyncFlipBegin' 'AsyncFlipCheckEnd' 'AsyncFlipEnd'
