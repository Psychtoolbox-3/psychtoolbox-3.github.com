# [BasicSoundScheduleDemo](BasicSoundScheduleDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[BasicSoundScheduleDemo](BasicSoundScheduleDemo)([wavfilenames])  
  
### This demo shows two things:  
  
- How to use audio schedules in [PsychPortAudio](PsychPortAudio) to preprogram a sequence  
of different sounds to play and how to dynamically add new sounds to the  
schedule while it is playing. This is similar to "playlists" in typical  
audio player applications like iTunes or the iPod etc.  
  
- How to create and use many prefilled audio buffers before start of a  
session. This way you can preload all needed sounds before start of an  
experiment into memory, in a format optimized for fast playback and low  
memory usage. This is similar to the concept of textures or offscreen  
windows in the domain of [Screen](Screen)() for the visuals.  
  
### Optional arguments:  
  
wavfilenames = Name of a .wav sound file to load and play back, or a cell  
array with multiple filenames to load. Otherwise the default sound files  
provided with Psychtoolbox will be loaded.  
  
The demo first loads all soundfiles, and resamples them to identical  
samplingrate if possible. Then it plays the first second of each of them.  
Then it goes into an interactive mode: By pressing any of the F1 - F10  
keys or any letter key, you can select a specific file for playback. By  
pressing any other key you exit the interactive loop. After the  
interactive loop has finished, a subset of the soundfiles is played again  
with a different method, for about 3 repetitions. Then the demo exits.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/BasicSoundScheduleDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/BasicSoundScheduleDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/BasicSoundScheduleDemo.m</code>
</div>

