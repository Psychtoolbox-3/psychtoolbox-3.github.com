# [SimpleVoiceTriggerDemo](SimpleVoiceTriggerDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[SimpleVoiceTriggerDemo](SimpleVoiceTriggerDemo)(triggerlevel)  
  
Demonstrates very basic usage of the new Psychtoolbox sound driver  
[PsychPortAudio](PsychPortAudio)() for implementation of a "voice trigger". This really  
only collects the "voice response time" it doesn't actually store the  
resonse itself. Have a look at [BasicSoundInputDemo](BasicSoundInputDemo) for how one can  
actually retrieve and save the sound vector with the response itself.  
  
The script relies on well working sound cards and drivers. It should  
"just work" on most [MacOS](MacOS)/X and Linux systems with standard hardware, but  
it will need special ASIO capable sound hardware on MS-Windows for  
accurate timing! See "help [InitializePsychSound](InitializePsychSound)" for details.  
  
In any case you \*must\* verify correct timing of your sound hardware with  
some external measurement equipment, e.g., in conjunction with the  
[PsychPortAudioTimingTest](PsychPortAudioTimingTest) script (or the [AudioFeedbackLatencyTest](AudioFeedbackLatencyTest) for a  
crude test). You only need to do this once after major changes to your  
systems software, hardware or Psychtoolbox installation, but there isn't  
any sane way to avoid such a validation!  
  
There are two different methods demonstrated to do so. Please read the  
source code of this file for details.  
  
### In method I:  
  
The "response window" is fixed to 5 seconds. A trial will always last 5  
seconds, regardless if you respond early, late, or not at all.  
  
  
### In method II:  
  
Sound is captured from the default recording device, waiting  
until the amplitude exceeds some 'triggerlevel'.  
  
If the triggerlevel is exceeded, sound capture stops, returning the  
estimated time of "voice onset" in system time.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/SimpleVoiceTriggerDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/SimpleVoiceTriggerDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/SimpleVoiceTriggerDemo.m</code>
</div>

