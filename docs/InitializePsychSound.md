# [InitializePsychSound](InitializePsychSound)
##### >[Psychtoolbox](Psychtoolbox)>[PsychSound](PsychSound)

[InitializePsychSound](InitializePsychSound)([reallyneedlowlatency=0])  
  
This routine loads the [PsychPortAudio](PsychPortAudio) sound driver for high-precision,  
low-latency, multi-channel sound playback and recording.  
  
Call it at the beginning of your experiment script, optionally providing  
the 'reallyneedlowlatency' flag set to one to push really hard for low  
latency.  
  
On [MacOS](MacOS)/X and GNU/Linux, the [PsychPortAudio](PsychPortAudio) driver will just work with  
the lowest possible latency and highest timing precision after this  
initialization.  
  
### On Microsoft Windows, things are more complicated and painful as always:  
  
[PsychPortAudio](PsychPortAudio) on Windows supports three different Windows sound systems,  
MME, [DirectSound](DirectSound) and ASIO. Only ASIO is suitable for research grade  
auditory stimulation with support for multi-channel sound cards and for  
high-precision and low-latency sound timing and time-stamping. If you  
want reliable timing and time-stamping with latencies and accuracy better  
than 500 msecs, you \*must\* have a decent ASIO sound card with proper  
vendor supplied ASIO drivers installed in your computer. A regular card,  
for example built-in sound chips of your computer, will not suffice and  
we will not guarantee any reasonable timing precision at all!  
  
The Windows MME [(MultiMediaExtensions)]((MultiMediaExtensions)) sound system has typical latencies  
and inaccuracies in excess of 500 msecs, and the slightly better  
[DirectSound](DirectSound) sound system still has a typical latency of over 30  
milliseconds. Both systems are known to be buggy and unreliable wrt.  
timing on many systems.  
  
The ASIO sound system provided by professional class sound cards usually  
has excellent timing precision and latencies below 15 msecs, often as low  
as 5 msecs for pro hardware. If you need really low latency or high  
precision sound on Windows, ASIO is what you must use: Some (usually more  
expensive) professional class sound cards ship with ASIO enabled sound  
drivers, or at least there's such a driver available from the support  
area of the website of your sound card vendor.  
  
Disclaimer: "ASIO is a trademark and software of Steinberg Media  
Technologies [GmbH](GmbH)."  
  
For cards without native ASIO drivers, there's the free ASIO4ALL driver,  
downloadable from http://asio4all.com, which may or may not work well on  
your specific sound card - The driver emulates the ASIO interface on top  
of the WDM-KS (Windows Driver Model Kernel Streaming) API from Microsoft,  
so the quality depends on the underlying WDM driver. For research grade  
use, please do yourself a favor and invest in a real ASIO card.  
  
If you manage to get such an ASIO enabled sound driver working on your  
sound hardware, and your ASIO enabled driver and sound card are of  
sufficiently high quality, you can enjoy latencies as low as 5 msecs and  
a sound onset accuracy with a standard deviation from the mean of less  
than 0.1 milliseconds on MS-Windows - We measured around 20 microseconds  
on some setups, e.g., the M-Audio Delta 1010-LT soundcard under  
Windows-XP SP2.  
  
Using OS/X or Linux will usually get you comparably good or better  
results with most standard sound hardware, due to the technically  
superior sound systems of these operating systems.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychSound/InitializePsychSound.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychSound/InitializePsychSound.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychSound/InitializePsychSound.m</code>
</div>

