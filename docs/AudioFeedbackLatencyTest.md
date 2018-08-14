# [AudioFeedbackLatencyTest](AudioFeedbackLatencyTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[AudioFeedbackLatencyTest](AudioFeedbackLatencyTest)([trigger=0.1] [, nrtrials=10] [, freq=44100][, freqout=44100][, runmode=1])  
  
Tries to test sound onset accuracy of [PsychPortAudio](PsychPortAudio) without need for  
external measurement equipment: Sound signals are played back via  
[PsychPortAudio](PsychPortAudio) at well defined points in time, using low-latency mode. At  
the same time, sound is captured via PsychPortAudio's capture facilities.  
The idea is that the microphone or line-in connector should pick up and  
capture the sound signals emitted through line-out (via a line-out -\>  
line-in feedback cable) or emitted through the speakers. We measure and  
compare timing of emitted vs. captured sound spikes.  
  
Results on [MacbookPro](MacbookPro) suggest that the method works, but with a not 100%  
accuracy, so its still better to use external measurement equipment to  
test!!!  
  
EARLY BETA CODE: DON'T USE OR USE WITH GREAT CAUTION!  
  
Optional parameters:  
'trigger' = Trigger level for detection of sound onset in captured sound.  
  
'ntrials' = Number of measurement trials to perform.  
  
'freq' = Samplerate of capture device.  
  
'freqout' = Samplerate of playback device.  
  
Obviously this test function can only be used in a very silent room!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/AudioFeedbackLatencyTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/AudioFeedbackLatencyTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/AudioFeedbackLatencyTest.m</code>
</div>

