# [DatapixxAudioKey](DatapixxAudioKey)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[DatapixxToolbox](DatapixxToolbox)>[DatapixxBasic](DatapixxBasic)

[DatapixxAudioKey](DatapixxAudioKey) - A prototype implementation of a [DataPixx](DataPixx)  
audio-key/voice-key.  
  
This allows to record audio from the Datapixx, optionally synchronized to  
visual stimulus onset, optionally with simple but precise timestamping of  
onset of audio signals.  
  
This is an experimental proof-of-concept prototype! Its name, behaviour  
and interface may change without warning in future beta-releases!  
  
  
# Subfunctions and their meaning  
  
[DatapixxAudioKey](DatapixxAudioKey)('Open' [, sampleRate][, lrMode][, inputJack][, inputGain]);  
- Open audio system for recording. This will stop any running audio  
acquisition operations. Audio sampling will be performed at the given  
optional 'sampleRate' between 8000 Hz and 96Khz with the given number of  
audio input channels 'lrMode' (0 = Mono: Average of left and right  
channel, 1 = Only left channel, 2 = Only right channel, 3 = Stereo).  
Optionally select 'inputJack' as audio input (1=Microphone, 2=Line-In)  
and 'inputGain' as input amplifier gain. If no 'inputJack' is specified  
and no input is preselected, 'inputJack' will default to microphone  
input.  
  
  
[DatapixxAudioKey](DatapixxAudioKey)('[Close](Close)');  
- [Close](Close) audio subsystem after stopping any running acquisition operations.  
  
[startTimeBox, startTimeGetSecs] = [DatapixxAudioKey](DatapixxAudioKey)('CaptureNow' [, maxDurationSecs=30][, startOffsetSecs=0][,bufferBaseAddress=20e6] [, numBufferFrames=maxScheduleFrames]);  
- Start audio capture immediately (ie., with minimum possible delay on  
your system), return a 'startTimeBox' timestamp in Datapixx clock time of  
when capture actually started or will start, taking the 'startOffsetSecs'  
into account. You can also use the 2nd optional return argument  
'startTimeGetSecs' to get the same timestamp mapped to Psychtoolbox  
[GetSecs](GetSecs)() time. For a more precise mapping to [GetSecs](GetSecs) time, you can  
convert the 'startTimeBox' timestamp into Psychtoolbox [GetSecs](GetSecs)() time  
with the proper mapping functions of [PsychDataPixx](PsychDataPixx) (see "help  
[PsychDataPixx](PsychDataPixx)").  
  
The optional 'startOffsetSecs' allows to delay the start of the capture  
operation by 'startOffsetSecs' seconds. The optional 'maxDurationSecs'  
allows to define an upper limit onto the duration of the audio capture  
operation. The operation will stop automatically after the given number  
of seconds. By default, capture will run for 30 seconds. For  
robustness and efficiency, you should specify a reasonable upper limit if  
possible. 'bufferBaseAddress' is the memory start address of the audio  
buffer for capture, 'numBufferFrames' is the size of the buffer. See  
"Datapixx [SetAudioSchedule](SetAudioSchedule)?" for more info. Leave at default settings if  
possible.  
  
  
[DatapixxAudioKey](DatapixxAudioKey)('CaptureAtFlip'[, flipCount=next][, maxDurationSecs=30][, startOffsetSecs=0][,bufferBaseAddress=20e6] [, numBufferFrames=maxScheduleFrames]);  
- Schedule start of audio capture synchronized to the visual stimulus  
onset of a future [Screen](Screen)('[Flip](Flip)') or [Screen](Screen)('AsyncFlipBegin') command.  
All parameters are identical to the ones for [DatapixxAudioKey](DatapixxAudioKey)('CaptureNow',...),  
except for the first optional parameter 'flipCount'. 'flipCount' defines  
at which [Screen](Screen)('[Flip](Flip)') audio capture should be started. If omitted or  
set to zero or [], capture will be triggered by the next flip command.  
Otherwise it will be triggered by the flip command with the given  
'flipCount'. You can query the current flipCount via [PsychDatapixx](PsychDatapixx)('FlipCount').  
  
Example: Setting flipCount = [PsychDatapixx](PsychDatapixx)('FlipCount') + 10; would start  
audio capture at the 10'th invocation of a flip command from now.  
  
This function doesn't return a capture start timestamp as capture will  
only happen in the future, so the timestamp is only available in the  
future.  
  
  
[audiodata, onsetTimeSecs] = [DatapixxAudioKey](DatapixxAudioKey)('GetResponse'[, amountSecs=current][, blocking=1][, stopCapture=0]);  
- Try to fetch available captured audiodata from a running capture  
operation. Only call this function after a capture operation has been  
started via [DatapixxAudioKey](DatapixxAudioKey)('CaptureNow') or scheduled for start at a  
certain flipCount via [DatapixxAudioKey](DatapixxAudioKey)('CaptureAtFlip') and the flip is  
imminent, i.e., after the flip command for that flip has been called  
already. The function will error-out if you call it too early!  
  
The optional 'amountSecs' asks the driver to return exactly  
'amountSecs' worth of audio data. By default it will return whatever  
is available at time of call. If 'amountSecs' is specified, but the  
requested amount is not yet available, the optional 'blocking' flag will  
define behaviour: If set to 1 (default), the driver will wait until the  
specified amount becomes available. If set to 0, the driver will return  
with empty [] return arguments so you can retry later. The optional  
'stopCapture' flag if set to 1 will stop audio capture, its default  
setting of zero will keep capture running until manually stopped or until  
it stops by itself.  
  
'audiodata' is the vector or matrix of captured audiodata. 1 Row for mono  
recording, or a 2-row matrix (one row for each audio channel) in stereo  
recording modes. Each value is an audio signal sample in range [-1 ; 1].  
  
'onsetTimeSecs' is the time since start of audio capture when a certain  
level of loudness (as set by [DatapixxAudioKey](DatapixxAudioKey)('TriggerLevel')) was first  
exceeded, e.g., due to onset of a vocal response of a subject.  
  
'readOffset' is the sample index of the next sample that will be read on  
the next call to this function, if any.  
  
  
oldLevel = [DatapixxAudioKey](DatapixxAudioKey)('TriggerLevel' [, newLevel]);  
- Return old and optionally set new trigger threshold level for the  
timestamping of onset of audio signals in [DatapixxAudioKey](DatapixxAudioKey)('GetResponse').  
  
'oldLevel' is the current/old level. 'newLevel' is the optional new  
level. Level can be between 0 and 1, with a default level of 0.1 for 10%  
of max signal intensity as trigger level.  
  
  
[DatapixxAudioKey](DatapixxAudioKey)('AutoTriggerLevel', silenceSecs);  
- Auto-Select trigger threshold level for audio onset timestamping. After  
start of audio capture, there must be a period of silence, where the only  
signal recorded is due to noise in the microphone/amplifiers etc, not due  
to actual signal. You must provide the minimum duration of this time  
period of silence as 'silenceSecs' parameter, e.g., 1.5 for 1.5 seconds  
of guaranteed silence at start of recording. During recording, the  
function will use this chunk of silence to compute an optimal trigger  
level, which is 10% louder than the loudest sample in the silence block  
and then use that triggerlevel as if [DatapixxAudioKey](DatapixxAudioKey)('TriggerLevel') had  
been called with that auto-selected level.  
  
  
[DatapixxAudioKey](DatapixxAudioKey)('StopCapture');  
- Stop audio capture as soon as possible.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/DatapixxAudioKey.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/DatapixxAudioKey.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/DatapixxToolbox/DatapixxBasic/DatapixxAudioKey.m</code>
</div>

