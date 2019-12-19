# [PsychPhotodiode](PsychPhotodiode)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[PsychPhotodiode](PsychPhotodiode) - Measure visual stimulus onset via photo-diodes and [PsychPortAudio](PsychPortAudio).  
  
Record a signal from a photo-diode connected to the audio input of a  
soundcard via [PsychPortAudio](PsychPortAudio), and timestamp the signal to compute a  
stimulus onset timestamp from the light flash picked up by the  
photo-diode.  
  
Iow. we abuse the sound card as a mini-oszillograph with automatic timestamping.  
  
# Subfunctions and their meaning  
  
pdiode = [PsychPhotodiode](PsychPhotodiode)('Open' [deviceIndex][, sampleRate][, lrMode]);  
- Open audio device 'deviceIndex' for recording. Audio sampling will be  
performed at the given optional 'sampleRate' with the given number of  
audio input channels. 'lrMode' (0 = Mono: Sum of left and right channel,  
1 = Only left channel, 2 = Only right channel, 3 = Average of channels).  
  
  
[PsychPhotodiode](PsychPhotodiode)('[Close](Close)', pdiode);  
- [Close](Close) audio device.  
  
  
startTime = [PsychPhotodiode](PsychPhotodiode)('Start', pdiode [, maxDurationSecs=3]);  
- Start audio capture immediately (ie., with minimum possible delay on  
your system), return a 'startTime' timestamp of when capture actually started  
or will start.  
  
The option 'maxDurationSecs' allows to define an upper limit onto the duration  
of the capture operation. The operation will stop automatically after the  
given number of seconds. By default, the capture will run for 3 seconds.  
  
  
[onsetTimeSecs, audiodata, rawaudiodata] = [PsychPhotodiode](PsychPhotodiode)('WaitSignal', pdiode [, maxWaitTime=maxDurationSecs][, blocking=1]);  
- Wait for stimulus onset, as picked up from a running capture operation.  
Only call this function after a capture operation has been started via  
[PsychPhotodiode](PsychPhotodiode)('Start'), or it will error out.  
  
The optional 'maxWaitTime' asks the driver to wait at most 'maxWaitTime'  
seconds for stimulus onset. By default it will wait up to as many seconds  
as set in the [PsychPhotodiode](PsychPhotodiode)('Start').  
  
If stimulus onset has not happened yet and 'maxWaitTime' has not been  
exceeded either, then the optional 'blocking' flag will define behaviour:  
If set to 1 (or omitted), the driver will wait until stimulus onset or  
timeout. If set to 0, the driver will return with empty [] return arguments  
so you can retry later with another call to [PsychPhotodiode](PsychPhotodiode)('WaitSignal').  
  
On return from 'WaitSignal', data capture / waiting for a signal will  
stop, unless 'blocking' was set to zero for polling and nothing was  
picked up yet.  
  
'onsetTimeSecs' is the system (=[GetSecs)](GetSecs)) time when a certain signal  
strength (as set by [PsychPhotodiode](PsychPhotodiode)('TriggerLevel') or more likely by  
[PsychPhotodiode](PsychPhotodiode)('CalibrateTriggerLevel')) was first exceeded since the  
last call to [PsychPhotodiode](PsychPhotodiode)('Start'), ie. most likely due to onset of the  
visual stimulus and corresponding light flash picked up by the photo-diode  
and sent as a voltage spike to the soundcard input.  
  
'audiodata' is the preprocessed row-vector of audiodata, used for  
actual timestamping.  
  
'rawaudiodata' is the vector or matrix of captured audiodata. 1 row for mono  
recording, or a 2-row matrix (one row for each audio channel) in stereo  
recording modes. Each value is an audio signal sample in range [-1 ; 1].  
  
  
oldLevel = [PsychPhotodiode](PsychPhotodiode)('TriggerLevel', pdiode [, newLevel]);  
- Return old and optionally set new trigger threshold level for the  
timestamping of onset of signals in [PsychPhotodiode](PsychPhotodiode)('GetResponse').  
  
'oldLevel' is the current/old level. 'newLevel' is the optional new  
level. Level can be between 0 and 1, with a default level of 0.1 for 10%  
of max signal intensity as trigger level.  
  
  
newLevel = [PsychPhotodiode](PsychPhotodiode)('CalibrateTriggerLevel', pdiode [, window][, triggerMult]);  
- Auto-Calibrate trigger threshold level for signal onset timestamping.  
  
Returns the found triggerLevel in 'newLevel'.  
  
### If the optional 'window' onscreen window handle is omitted, then:  
  
This captures signal for 3 seconds, assuming the photo-diode(s) point to an  
idle screen with black/background color. From that an optimal trigger level  
is computed and assigned, which is 'triggerMult' times higher than the brightest  
sample in the recorded "darkness" block and then use that triggerlevel as if  
[PsychPhotodiode](PsychPhotodiode)('TriggerLevel') had been called with that auto-selected level.  
'triggerMult' defaults to 20 if omitted.  
  
### If the optional 'window' onscreen window handle is provided, then:  
  
First the window is turned completely black, 3 seconds of "darkness" are  
captured and maximum signal at black is computed. Then the window is  
turned fully bright white, 3 seconds of "lightness" are captured and  
maximum white signal is computed. Then the window goes dark again, and  
the optimal triggerLevel is computed as weighted average of dark max  
signal and white max signal, with 'triggerMult' defining the weighting  
between 0.0 and 1.0. 'triggerMult' defaults to the reasonable value 0.5  
if omitted.  
  
  
[PsychPhotodiode](PsychPhotodiode)('Stop', pdiode);  
- Stop capture as soon as possible.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychPhotodiode.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychPhotodiode.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychPhotodiode.m</code>
</div>

