# [Screen('Flip')](Screen-Flip) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


[Flip](Flip) front and back display surfaces in sync with vertical retrace and return  
completion timestamps.  
"windowPtr" is the id of the onscreen window whose content should be shown at  
flip time. "when" specifies when to flip: If set to zero (default), it will flip  
on the next possible video retrace. If set to a value when \> 0, it will flip at  
the first video retrace after system time 'when' has been reached. "dontclear"  
If set to 1, flip will not clear the framebuffer after [Flip](Flip) - this allows  
incremental drawing of stimuli. The default is zero, which will clear the  
framebuffer to background color after each flip. A value of 2 will prevent [Flip](Flip)  
from doing anything to the framebuffer after flip. This leaves the job of  
setting up the buffer to you - the framebuffer is in an undefined state after  
flip. "dontsync" If set to zero (default), [Flip](Flip) will sync to the vertical  
retrace and will pause execution of your script until the [Flip](Flip) has happened. If  
set to 1, [Flip](Flip) will still synchronize stimulus onset to the vertical retrace,  
but will \*not\* wait for the flip to happen: [Flip](Flip) returns immediately and all  
returned timestamps are invalid. A value of 2 will cause [Flip](Flip) to show the  
stimulus \*immediately\* without waiting/syncing to the vertical retrace.  
"multiflip" defaults to zero: If set to a value greater than zero, [Flip](Flip) will  
flip \*all\* onscreen windows instead of just the specified one. This allows to  
synchronize stimulus onset on multiple displays, e.g., for multidisplay stereo  
setups or haploscopes. You need to (somehow) synchronize all attached displays  
for this to operate tear-free. [Flip](Flip) (optionally) returns a high-precision  
estimate of the system time (in seconds) when the actual flip has happened in  
the return argument 'VBLTimestamp'. An estimate of Stimulus-onset time is  
returned in 'StimulusOnsetTime'. Beampos is the position of the monitor scanning  
beam when the time measurement was taken (useful for correctness tests).  
[FlipTimestamp](FlipTimestamp) is a timestamp taken at the end of [Flip](Flip)'s execution. Use the  
difference between [FlipTimestamp](FlipTimestamp) and [VBLTimestamp](VBLTimestamp) to get an estimate of how long  
Flips execution takes. This is useful to get a feeling for the timing error if  
you try to sync script execution to the retrace, e.g., for triggering  
acquisition devices like EEG, fMRI, or for starting playback of a sound.  
"Missed" indicates if the requested presentation deadline for your stimulus has  
been missed. A negative value means that dead- lines have been satisfied.  
Positive values indicate a deadline-miss. The automatic detection of  
deadline-miss is not fool-proof - it can report false positives and also false  
negatives, although it should work fairly well with most experimental setups. If  
you are picky about timing, please use the provided timestamps or additional  
methods to exercise your own tests.   


###See also:
[DrawingFinished](Screen-DrawingFinished) [WaitUntilAsyncFlipCertain](Screen-WaitUntilAsyncFlipCertain) [AsyncFlipBegin](Screen-AsyncFlipBegin) [AsyncFlipCheckEnd](Screen-AsyncFlipCheckEnd) [AsyncFlipEnd](Screen-AsyncFlipEnd) Flip
