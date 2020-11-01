# [AudioFeedbackLatencyTest](AudioFeedbackLatencyTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[AudioFeedbackLatencyTest](AudioFeedbackLatencyTest)([roundtrip=0][, trigger=0.1] [, nrtrials=10] [, freq=44100][, freqout=44100][, fullduplex=0][, runmode=1])  
  
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
  
### EARLY BETA CODE: USE ONLY WITH GREAT CAUTION AND SUSPICION!  
  
### Optional parameters:  
  
'roundtrip' If set to 0 then this measures scheduling accuracy of sound  
onset, as measured by sound capture -- should be no worse than ~ 1 msec  
on a well working system, and input detection latency, ie., how long does  
it take from physical sound onset to detection of sound onset by the  
script. This would be a useful measure of how fast a "Voicekey" could  
respond to voice onset in a best case scenario.  
  
If set to 1 then this measures time from issuing the [PsychPortAudio](PsychPortAudio)('Start')  
command to start playback until actual start of playback (by driver self-  
assessment, and by measuring via audio capture), and also as "Roundtrip"  
how long it would take to detect the onset by the script.  
  
'trigger' = Trigger level for detection of sound onset in captured sound.  
  
'ntrials' = Number of measurement trials to perform.  
  
'freq' = Samplerate of capture device.  
  
'freqout' = Samplerate of playback device.  
  
'fullduplex' = Use soundcard in full-duplex mode.  
  
'runmode' = Runmode for [PsychPortAudio](PsychPortAudio) to choose.  
  
Obviously this test function can only be used in a very silent room!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/AudioFeedbackLatencyTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/AudioFeedbackLatencyTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/AudioFeedbackLatencyTest.m</code>
</div>

