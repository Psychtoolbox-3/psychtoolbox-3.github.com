# [DelayedSoundFeedbackDemo](DelayedSoundFeedbackDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[DelayedSoundFeedbackDemo](DelayedSoundFeedbackDemo)([reqlatency=150 ms][, duplex=0][, freq = 48000][, minLatency= 10 ms])  
  
### CAUTION: TEST TIMING OF THIS SCRIPT WITH MEASUREMENT EQUIPMENT IF YOU  
DEPEND ON ACCURATE FEEDBACK TIMING!!!  
  
Demonstrates usage of the new Psychtoolbox sound driver [PsychPortAudio](PsychPortAudio)()  
for audio feedback with a controlled delay.  
  
Sound is captured from the default recording device and then - with a  
selectable delay - played back via the default output device.  
  
### Parameters and their meaning:  
  
'reqlatency' Wanted feedback latency between sound input and output in  
milliseconds. A value of zero will ask for the lowest possible latency on  
the given setup. Defaults to 150 msecs. Please notice that the minimum  
achievable latency will be constrained by the capabilities of your  
operating system, sound card driver, computer hardware and sound  
hardware. Only very high quality systems will be able to go below 5 msecs  
latency, good systems will be able to go below 20 msecs, but less capable  
setups may only allow for a latency much larger than 20 msecs. In order  
to achieve low latency reliably without timing glitches or audible  
artifacts, you may need to tune both the parameters for this demo and  
your system setup carefully. The optimal parameter set varies from setup  
to setup.  
  
### 'duplex' = Select between full-duplex and half-duplex mode:  
  
Depending on your sound hardware you'll have to either leave 'duplex' at  
its default of zero (2 times half-duplex mode, aka simplex mode) or set  
it to 1 (full-duplex mode). On a given system, only one of these will work  
reliably (or at all): ASIO audio hardware -- typically on MS-Windows --  
will usually need full-duplex mode and won't work at all in simplex mode.  
On Macintosh OS/X it depends on the sound hardware. [IntelMacs](IntelMacs) are happy  
with half-duplex mode, some [PowerMacs](PowerMacs) may need full-duplex mode. However,  
except for 'reqlatency' == 0 minimal latency mode, simplex mode provides  
much higher accuracy and reliability on OS/X at least with the built-in  
soundchips on Intel based Macintosh computers. On Linux, performance  
varies depending on the card at use.  
  
'freq' = Sampling frequency (Hz). Defaults to 48000 Hz as this rate is  
most commonly supported on most sound hardware. The maximum achievable  
value depends on your specific soundcard. IntelMac's built in soundchips  
allow for a maximum of 96000 Hz, high-end soundcards may allow for 192000  
Hz under some circumstances. Increasing the frequency reduces minimum  
latency but increases system load and the probability of glitches.  
  
'minLatency' is a tuning parameter for the driver and a hard-constraint  
on the mininum achievable latency for feedback. It is ignored on OS/X,  
but can be tused for tuning latency vs. reliability on Linux and on  
MS-Windows. High-end cards may allow for much lower than the default 10  
msecs, low-end cards may malfunction at lower settings. Non-ASIO  
soundcards on MS-Windows will likely fail already at much higher settings  
and be therefore completely unsuitabe for low latency feedback.  
  
### Specific tips for different setups:  
  
On OS/X with builtin soundchip on [IntelMacs](IntelMacs), choose duplex = 0 for  
feedback with controlled low-latency, and a freq'ency of 96000 Hz. For  
lowest latency mode, you may try reqlatency = 0 and duplex = 1.  
  
On MS-Windows you \*must\* use a soundcard with ASIO support for any  
reasonable results! Here you should always set duplex = 1 for full-duplex  
operation, anything else will fail. Use reqlatency = 0 for feedback with  
minimal latency, positive values for feedback with controlled latency.  
Play around with the 'minLatency' parameter, set it as low as possible -  
to the lowest value that doesn't cause any error messages by our driver  
or audible artifacts like crackling noises or static. Try to set  
'freq'uency as high as possible. Check the manual of your soundcard for  
the highest value that can be used for capture + playback. E.g., the  
Soundblaster Audigy ZS 2 seems to be limited to max. 48000 Hz in this  
mode.  
  
On Linux, no general statements can be made, only that some soundcards  
allow for extremely low latencies of < 2 msecs if properly tuned. Search  
the Internet for tips.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/DelayedSoundFeedbackDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/DelayedSoundFeedbackDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/DelayedSoundFeedbackDemo.m</code>
</div>

