# [Snd](Snd)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

err = [Snd](Snd)(command,[signal],[rate],[sampleSize])  
  
Old Sound driver for Psychtoolbox. USE OF THIS DRIVER IS DEPRECATED FOR  
ALL BUT THE MOST TRIVIAL PURPOSES! Only useful for simple feedback tones,  
and indirectly by Eyelink's calibration routines. Does not mix well with  
simultaneous use of [PsychPortAudio](PsychPortAudio)() or [Screen](Screen)() movie playback functions!  
  
Have a look at the help for [PsychPortAudio](PsychPortAudio) ("help [PsychPortAudio](PsychPortAudio)" and  
"help [InitializePsychSound](InitializePsychSound)") for an introduction into the new sound  
driver, which is recommended for most purposes.  
  
[Snd](Snd)() is a rather dumb and primitive wrapper around the [PsychPortAudio](PsychPortAudio)()  
driver. It uses PsychPortAudio's most basic functionality to achieve  
"sort of ok" sound playback. The driver is used in high latency, low timing  
precision mode, so [Snd](Snd)()'s audio playback timing will likely be very unreliable.  
  
Alternatively you can create an empty file named '[Snd](Snd)\_use\_oldstyle.txt' in  
the [PsychtoolboxConfigDir](PsychtoolboxConfigDir)() folder, ie., [[PsychtoolboxConfigDir](PsychtoolboxConfigDir) '[Snd](Snd)\_use\_oldstyle.txt']  
This will enable the old-style implementation of [Snd](Snd)(), which just calls into  
Matlabs/Octaves sound() function. As sound() is of varying quality, there may  
be bugs, latency- and timing problems associated with the use of sound() by [Snd](Snd)().  
  
The command [Snd](Snd)('Oldstyle') also requests use of this old-style sound() path.  
  
# Audio device sharing for interop with [PsychPortAudio](PsychPortAudio)  
  
If you want to use [PsychPortAudio](PsychPortAudio) and [Snd](Snd)() simultaneously, or one of the  
functions that indirectly use [Snd](Snd)(), e.g., [Beeper](Beeper)() for simple beep tones,  
or Eyelink's auditory feedback during tracker setup and recalibration, which  
in turn uses [Beeper](Beeper)() and thereby [Snd](Snd)(), then try this:  
  
1. Open a suitable [PsychPortAudio](PsychPortAudio) audio device, possibly also a slave audio  
   device and get a pahandle to it, e.g., pahandle = [PsychPortAudio](PsychPortAudio)('Open',...);  
   or [PsychPortAudio](PsychPortAudio)('OpenSlave', ...) for a slave device.  
  
2. Now open [Snd](Snd)(), passing in this device handle for use as [Snd](Snd)() output device:  
   [Snd](Snd)('Open', pahandle);  
  
   If you want to repeatedly call [Beeper](Beeper)(), or use auditory feedback from Eyelink,  
   which itself repeatedly calls [Beeper](Beeper)(), then you should open the shared pahandle  
   via [Snd](Snd)('Open', pahandle, 1); - This will prevent [Snd](Snd)('[Close](Close)') from having any  
   effect, so [Beeper](Beeper)() won't close the [Snd](Snd)() driver after one beep, and Eyelink  
   will be able to emit multiple auditory feedback tones, not just a single one.  
  
3. Proceed as usual, e.g., [Snd](Snd)('Play', ...) or [Beeper](Beeper)(...), etc. [Snd](Snd)() will  
   use the pahandle audio device for playback, and pahandle can also be used  
   by [PsychPortAudio](PsychPortAudio) calls directly for precisely controlled sound.  
  
4. At the end of a session, you could forcefully detach [Snd](Snd)() from the pahandle  
   via a call to [Snd](Snd)('[Close](Close)', 1).  
  
# Supported functions  
  
[Snd](Snd)('Play', signal [, rate][, sampleSize]) plays a sound.  
  
rate=[Snd](Snd)('DefaultRate') returns the default sampling rate in Hz, which  
currently is 22254.5454545454 Hz on all platforms for the old style sound  
implementation, and the default device sampling rate if [PsychPortAudio](PsychPortAudio) is  
used. This default may change in the future, so please either specify a  
rate, or use this function to get the default rate. (This default is  
suboptimal on any system except long dead [MacOS](MacOS)-9, but kept for backwards  
compatibility!).  
  
The optional 'sampleSize' argument used with [Snd](Snd)('Play') is only retained  
for backwards compatibility and has no meaning, unless you opt in to use  
the old-style implementation. Otherwise it is checked for correctness, but  
other than that it is ignored. Allowable values are either 8 or 16.  
  
oldverbosity = [Snd](Snd)('Verbosity' [, verbosity]);  
- Query current level of verbosity, optionally set a new 'verbosity' level.  
  
[Snd](Snd)('Open') opens the channel, which stays open until you call  
[Snd](Snd)('[Close](Close)'). [Snd](Snd)('Play',...) automatically opens the channel if it isn't  
already open. You can use [Snd](Snd)('Open', pahandle); to share an existing  
[PsychPortAudio](PsychPortAudio) audio device handle 'pahandle' with [Snd](Snd)() for optimal  
interoperation. A [Snd](Snd)('[Close](Close)') of such a shared 'pahandle' would not close the  
handle, but it would close [Snd](Snd)()'s further use of it. If you call  
[Snd](Snd)('Open', pahandle, 1); then a [Snd](Snd)('[Close](Close)') will not have any effect, ie. the  
pahandle not only stays open, but also continues to be shared and open for use  
by [Snd](Snd)(). See instructions above.  
  
[Snd](Snd)('[Close](Close)') immediately stops all sound and closes the channel, unless you  
specified a shared pahandle with [PsychPortAudio](PsychPortAudio) via [Snd](Snd)('Open', pahandle, 1);  
earlier. Calling [Snd](Snd)('[Close](Close)', 1) will always really close the channel.  
  
[Snd](Snd)('Wait') waits until the sound is done playing.  
  
isPlaying=[Snd](Snd)('IsPlaying') returns true if any sound is playing, and  
false (0) otherwise.  
  
[Snd](Snd)('Quiet') stops the sound currently playing, but leaves the channel open.  
  
"signal" must be a numeric array of samples.  
  
Your "signal" data should lie between -1 and 1 (smaller to play more  
softly). If the "signal" array has one row then it's played monaurally,  
through both speakers. If it has two rows then it's played in stereo.  
([Snd](Snd) has no provision for changing which speaker(s), or the volume, used  
by a named snd resource, so use READSND to get the snd into an array,  
and supply the appropriately modified array to [Snd](Snd).)  
  
"rate" is the rate (in Hz) at which the samples in "signal" should be  
played. We suggest you always specify the "rate" parameter. If not  
specified, the sample "rate", on all platforms, defaults to OS9's  
standard hardware sample rate of 22254.5454545454 Hz. That value is  
returned by [Snd](Snd)('DefaultRate'). Other values can be specified.  
  
OSX & WIN: "samplesize". [Snd](Snd) accepts the sampleSize argument and passes  
it to the Matlab SOUND command.  SOUND (and therefore [Snd](Snd) also) obeys the  
specified sampleSize value, either 8 or 16, only if it is supported by  
your computer hardware.  
  
[Snd](Snd)('Play',sin(0:10000)); % play 22 [KHz](KHz)/(2\*pi)=3.5 kHz tone  
[Snd](Snd)('Play',[sin(1:20000) zeros(1,10000);zeros(1,10000) sin(1:20000)]); % stereo  
[Snd](Snd)('Wait');              % wait until end of all sounds currently in channel  
[Snd](Snd)('Quiet');             % stop the sound and flush the queue  
  
For most of the commands, the returned value is zero when successful, and  
a nonzero error number when [Snd](Snd) fails.  
  
[Snd](Snd)('Play', signal) takes some time to open the channel, if it isn't  
already open, and allocate a snd structure for your sound. This overhead  
of the call to [Snd](Snd), if you call it in the middle of a movie, may be  
perceptible as a pause in the movie, which would be bad. However, the  
actual playing of the sound, asynchronously, is a background process that  
usually has very little overhead. So, even if you want a sound to begin  
after the movie starts, you should create a soundtrack for your entire  
movie duration (possibly including long silences), and call [Snd](Snd) to set  
the sound going before you start your movie. (Thanks to Liz Ching for  
raising the issue.)  
  
NOTE: We suggest you always specify the "rate" parameter. If not  
specified, the sample rate, on all platforms, defaults to OS9's  
standard hardware sample rate of 22254.5454545454 Hz. That value is returned  
by [Snd](Snd)('DefaultRate').  
  
See also [PsychPortAudio](PsychPortAudio), [Beeper](Beeper), AUDIOPLAYER, PLAY, [MakeBeep](MakeBeep), READSND, and WRITESND.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/Snd.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/Snd.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/Snd.m</code>
</div>

