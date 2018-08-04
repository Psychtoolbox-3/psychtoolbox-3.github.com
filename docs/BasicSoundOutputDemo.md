# [BasicSoundOutputDemo](BasicSoundOutputDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[BasicSoundOutputDemo](BasicSoundOutputDemo)([repetitions=0][, wavfilename])  
  
Demonstrates very basic use of the Psychtoolbox sound output driver  
[PsychPortAudio](PsychPortAudio)(). [PsychPortAudio](PsychPortAudio) is a better, more reliable, more accurate  
replacement for the old Psychtoolbox SND() function and other means of  
sound output in Matlab like sound(), soundsc(), wavplay(), audioplayer()  
etc.  
  
This demo only demonstrates normal operation, not the low-latency mode,  
extra demos and tests for low-latency and high precision timing output will  
follow soon. If you need low-latency, make sure to read "help  
[InitializePsychSound](InitializePsychSound)" carefully or contact the forum.  
Testing for low-latency mode showed that sub-millisecond accurate sound  
onset and < 10 msecs latency are possible on Linux, OSX and on some specially  
configured MS-Windows ASIO sound card setups.  
  
  
### Optional arguments:  
  
repetitions = Number of repetitions of the sound. Zero = Repeat forever  
(until stopped by keypress), 1 = Play once, 2 = Play twice, ....  
  
wavfilename = Name of a .wav sound file to load and playback. Otherwise  
the good ol' handel.mat file (part of Matlab) is used.  
  
The demo just loads and plays the soundfile, waits for a keypress to stop  
it, then quits.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/BasicSoundOutputDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/BasicSoundOutputDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/BasicSoundOutputDemo.m</code>
</div>

