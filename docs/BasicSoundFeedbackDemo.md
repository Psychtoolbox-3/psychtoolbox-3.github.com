# [BasicSoundFeedbackDemo](BasicSoundFeedbackDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[BasicSoundFeedbackDemo](BasicSoundFeedbackDemo)([reqlatency=7.5 ms] [,duplex=0])  
  
Demonstrates very basic usage of the new Psychtoolbox sound driver  
[PsychPortAudio](PsychPortAudio)() for audio feedback. For a more complex solution  
which provides much more precise audio feedback timing for control  
of audio feedback delay, look at [DelayedSoundFeedbackDemo](DelayedSoundFeedbackDemo) instead.  
  
Sound is captured from the default recording device and then - with a  
selectable delay - played back via the default output device.  
  
By default, feedback is tried with a latency of 7.5 ms plus hardware and  
system inherent delay, but you can ask for a specific latency in msecs by  
providing the optional parameter 'reqlatency'. Achievable latency will be  
constrained by the capabilities of your hardware. Choosing too low of a  
value will create audible artifacts in the sound and the driver may  
output warning about 'buffer underflows during streaming refill...'.  
  
Depending on your sound hardware you'll have to either leave 'duplex' at  
its default of zero (2 times half-duplex mode) or set it to 1  
(full-duplex mode): ASIO driven hardware -- typically on MS-Windows --  
will usually need full-duplex mode. On Macintosh OS/X it depends on the  
sound hardware. [IntelMacs](IntelMacs) are happy with half-duplex mode, some [PowerMacs](PowerMacs)  
may need full-duplex mode.  
  
  
If you need low-latency, make sure to read "help [InitializePsychSound](InitializePsychSound)"  
carefully or contact the forum.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/BasicSoundFeedbackDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/BasicSoundFeedbackDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/BasicSoundFeedbackDemo.m</code>
</div>

