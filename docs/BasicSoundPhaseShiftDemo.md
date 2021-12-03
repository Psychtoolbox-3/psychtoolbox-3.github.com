# [BasicSoundPhaseShiftDemo](BasicSoundPhaseShiftDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[BasicSoundPhaseShiftDemo](BasicSoundPhaseShiftDemo)([showit=1][, targetChannel=1])  
  
Demonstrates how one can play back a phase-shifted sine tone, with dynamically  
adjustable phase shift, free of audible artifacts during phase shift change.  
  
This uses PsychPortAudio's realtime mixing and some trigonometric math to  
synthesize a cosine wave of selectable phase in realtime from the weighted sum  
of a pair of a cosine + sine wave with different relative amplitudes.  
  
The sine wave is put into one sound channel. A cosine wave of same frequency  
(but 90 degrees phase-shifted) is put in another sound channel. Both sound  
channels are mixed together in realtime by [PsychPortAudio](PsychPortAudio), with controllable  
relative volume (== amplitude == mix-weight) for each of the two channels, and  
the result of this two-channel weighted mix is output to the 2nd audio output  
channel of the actual soundcard, creating a synthesized phase-shifted cosine  
wave of same frequency. Changing the relative channel volumes changes the phase  
shift of the cosine output wave in realtime, without artifacts / discontinuities.  
The proper relative volume levels are computed from the desired phase shift and  
set in the internal subfunction updatePhase() by the magic of math.  
  
A second reference sine wave is output to the 1st audio channel of the soundcard,  
if 'targetChannel' == 1, so one can drive two speakers / transducers, one outputting  
a phase-shifted sine wave, relative to th other speaker / transducer. For testing  
purposes, one can set 'targetChannel' == 2 to mix the reference sine-wave with the  
phase-shifted cosine wave both into output speaker channel 2, to simulate potential  
constructive / destructive interference between reference and phase-shifted sine  
wave. Setting 'showit' == 1 will capture the audio signal send to both soundcard  
channel and visualize it in a Psychtoolbox onscreen window, for illustrative purposes  
and for basic debugging. If you want to run a real auditory experiments, you'd use  
'targetChannel' == 1 and some external microphones and oscillograph to check for  
proper audio output independently of [PsychPortAudio](PsychPortAudio), Psychtoolbox and your computer.  
  
One use case for this are studies as described under this link...  
https://psychtoolbox.discourse.group/t/can-i-change-the-phase-of-a-sine-wave-with-psychportaudio/4086  
...more specifically experiments like this one about air conduction and bone conduction  
of sound:  
  
https://www.researchgate.net/publication/6535047\_Simultaneous\_cancellation\_of\_air\_and\_bone\_conduction\_tones\_at\_two\_frequencies\_Extension\_of\_the\_famous\_experiment\_by\_von\_Bekesy  
  
Have a look at [BasicAMAndMixScheduleDemo](BasicAMAndMixScheduleDemo) on how to apply amplitude modulation (AM)  
of signals by attaching AM modulator slave devices to the pafixedsine and pashiftsine  
slave devices used here. A suitable time series of AM envelope values would allow to  
gate the output sine waves.  
  
This demo was sponsored by a priority support request. Thanks!  
  
### Usage:  
  
ESCAPE key ends the demo.  
  
Left and right cursor keys allow to shift phase interactively.  
  
### Optional parameters:  
  
'showit' If set to 1, visualize actual output signals, channel 1 in red,  
         channel 2 in green. Defaults to 1 for showing output.  
  
'targetChannel' To which channel should the fixed phase reference signal be  
                output? 1 = channel 1 (default). 2 = channel 2 will output into  
                the same channel as the phase-shifted signal, so both signals  
                will show constructive or destructive interference, depending  
                on phase-shift of the 2nd signal which always goes to channel 2.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/BasicSoundPhaseShiftDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/BasicSoundPhaseShiftDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/BasicSoundPhaseShiftDemo.m</code>
</div>

