# [InitializePsychSound](InitializePsychSound)
##### >[Psychtoolbox](Psychtoolbox)>[PsychSound](PsychSound)

[InitializePsychSound](InitializePsychSound)([reallyneedlowlatency=0])  
  
This routine loads the [PsychPortAudio](PsychPortAudio) sound driver for high-precision,  
low-latency, multi-channel sound playback and recording.  
  
Call it at the beginning of your experiment script, optionally providing  
the 'reallyneedlowlatency' flag set to one to push really hard for low  
latency.  
  
On [MacOS](MacOS)/X and GNU/Linux, the [PsychPortAudio](PsychPortAudio) driver will just work with  
low latency and highest timing precision after this initialization.  
  
### On Microsoft Windows, things are a bit more complicated:  
  
[PsychPortAudio](PsychPortAudio) on Windows supports three different Windows sound systems,  
MME, WDM/KS and WASAPI. Only WDM/KS and WASAPI are suitable for research grade  
auditory stimulation with support for multi-channel sound cards and for  
high-precision and low-latency sound timing and time-stamping. If you  
want reliable timing and time-stamping with latencies and accuracy better  
than 500 msecs, you \*must\* use one of these. By default, in low latency mode,  
WASAPI is used on Windows Vista and later, whereas WDM/KS would be used on  
older Windows versions. WDM/KS is completely untested so far, and WASAPI has  
only been tested on Windows 7 and Windows 10. For best results, use of Windows 10  
is recommended.  
  
The Windows MME [(MultiMediaExtensions)]((MultiMediaExtensions)) sound system has typical latencies  
and inaccuracies as high as 500 msecs. WASAPI can achieve latencies as low  
as 10 msecs with onboard sound chips on Windows-10, and maybe even on Windows 8.1.  
On Windows 7 latencies around 20 msecs are possible. Timing should be generally  
accurate to millisecond level with WASAPI.  
  
Using OSX or Linux will usually get you at least as good, or usually better,  
results with most standard sound hardware, due to the technically superior  
sound systems of these operating systems.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychSound/InitializePsychSound.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychSound/InitializePsychSound.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychSound/InitializePsychSound.m</code>
</div>

