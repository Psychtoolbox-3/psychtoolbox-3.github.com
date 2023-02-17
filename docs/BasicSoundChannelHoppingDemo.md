# [BasicSoundChannelHoppingDemo](BasicSoundChannelHoppingDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[BasicSoundChannelHoppingDemo](BasicSoundChannelHoppingDemo)([nrChannels][, device])  
  
Opens a multi-channel sound card for output, then uses audio slave devices to  
output a mono beep tone to each audio output channel in succession, "sweeping"  
or "hopping" over all speakers / output channels of the sound card.  
  
Press and hold a key to exit.  
  
### Optional parameters:  
  
nrChannels = Number of channels to hop over. Tries to open first suitable audio  
device with nrChannels output channels if 'device' is omitted.  
  
device = Sound device index to choose. Will select 'device' by matching 'nrChannels'  
if omitted, or first audio device if both 'nrChannels' and 'device' are omitted.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/BasicSoundChannelHoppingDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/BasicSoundChannelHoppingDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/BasicSoundChannelHoppingDemo.m</code>
</div>

