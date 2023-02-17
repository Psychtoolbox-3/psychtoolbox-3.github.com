# [Screen('Flip')](Screen-Flip) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[VBLTimestamp StimulusOnsetTime FlipTimestamp Missed Beampos] = Screen('Flip', windowPtr [, when] [, dontclear] [, dontsync] [, multiflip]);

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
returned in 'StimulusOnsetTime'. Please note that the semantic and accuracy /  
reliability of the returned timestamps may differ if special display backends or  
display devices are in use. With the optional Vulkan display backend for special  
HDR, VRR or high bit depth display modes, the driver may only return estimated  
stimulus onset time, as an identical value in both 'StimulusOnsetTime' and in  
'VBLTimestamp'. Especially with special Virtual Reality (VR), Augmented Reality  
(AR) and Mixed Reality (MR) displays, commonly summarized under the name  
eXtended Reality (XR), usually only estimated stimulus onset time is returned,  
again in both 'StimulusOnsetTime' and in 'VBLTimestamp'. The robustness,  
trustworthiness, precision and accuracy of both returned stimulus onset  
timestamps and of adherence to the requested stimulus onset time "when" will  
vary greatly depending on the specific operating system, Psychtoolbox backend  
driver, vendor provided runtime driver and hardware. Also, precision often comes  
at the price of increased latency or lower performance or presentation  
framerates, depending on the tradeoffs you choose. Read the sections about  
timing, timestamping and precision vs. performance tradeoffs in 'help  
PsychVRHMD' carefully to understand what to expect and how to tune operations  
for your specific experimental needs if you use a VR/AR/MR/XR device.  
'Beampos' is the position of the monitor scanning beam when the time measurement  
was taken (useful for correctness tests). This value is only available on a  
subset of operating systems, graphics cards and display configurations. A  
constant value of -1 or zero means unsupported.  
'FlipTimestamp' is a timestamp taken at the end of [Flip](Flip)'s execution. Use the  
difference between [FlipTimestamp](FlipTimestamp) and [VBLTimestamp](VBLTimestamp) to get an estimate of how long  
Flips execution takes. This is useful to get a feeling for the timing error if  
you try to sync script execution to the retrace, e.g., for triggering  
acquisition devices like EEG, fMRI, or for starting playback of a sound.  
'Missed' indicates if the requested presentation deadline for your stimulus has  
been missed. A negative value means that deadlines have been satisfied. Positive  
values indicate a deadline-miss. The automatic detection of deadline-miss is not  
fool-proof - it can report false positives and also false negatives, although it  
should work fairly well with most experimental setups. If you are picky about  
timing, please use the provided timestamps or additional methods to exercise  
your own tests. In case of use of special display backends like Vulkan for VRR,  
HDR or high bit depth display modes, or when used with VR/AR/MR/XR displays the  
'Missed' value is meaningless or unreliable at the moment. It only makes sense  
in standard display modes on standard hardware at the moment.  
  


###See also:
[DrawingFinished](Screen-DrawingFinished) [WaitUntilAsyncFlipCertain](Screen-WaitUntilAsyncFlipCertain) [AsyncFlipBegin](Screen-AsyncFlipBegin) [AsyncFlipCheckEnd](Screen-AsyncFlipCheckEnd) [AsyncFlipEnd](Screen-AsyncFlipEnd) Flip
