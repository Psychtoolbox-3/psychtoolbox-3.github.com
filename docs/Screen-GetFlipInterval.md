# [Screen('GetFlipInterval')](Screen-GetFlipInterval) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Returns an estimate of the monitor flip interval for the specified onscreen  
window."windowPtr" is the handle of the onscreen window for which info should be  
returned. "nrSamples" If left out, the estimated interval from previous calls to  
[GetFlipInterval](GetFlipInterval) or from the initial calibration done during  
[Screen](Screen)('OpenWindow'...) is reported. If set to a value greater zero, PTB will  
perform a measurement loop to compute a good estimate. The loop will run until  
at least nrSamples valid samples have been taken and standard deviation of the  
measurement is below "stddev" seconds. A timeout value "timeout" can be set to  
abort the measurement after timeout seconds if the measurement doesn't converge  
for some reason. Timeout is 10 seconds and stddev is 50 microseconds by default.  
PTB automatically takes at least 50 valid samples when opening an  
onscreen-window, trying to achieve a standard deviation below 100 microseconds,  
but timing out after a maximum of 15 seconds. If you require very high  
precision, call this routine with values that suit your demands. The returned  
monitorRefreshInterval is in seconds, but has sub-millisecond accuracy. The real  
number of valid samples taken and the final standard deviation is returned as  
well. CAUTION: When using [OpenGL](OpenGL) flip-frame stereo (stereomode=1 in [OpenWindow)](OpenWindow))  
on ATI graphics hardware, the flip interval (as reported here) may be twice as  
long as the monitor refresh interval! Using Anti-Aliasing with a high  
multiSample level at a high display resolution may also cause the graphics  
hardware to switch to a flip-interval twice as long as the monitor refresh  
interval, because it is not capable of performing all anti-aliasing computations  
in one single refresh interval.   


###See also:
[OpenWindow](Screen-OpenWindow), Flip, [NominalFrameRate](Screen-NominalFrameRate)
