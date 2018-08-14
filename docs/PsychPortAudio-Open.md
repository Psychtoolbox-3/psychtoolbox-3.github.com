# [PsychPortAudio('Open')](PsychPortAudio-Open) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction


Open a [PortAudio](PortAudio) audio device and initialize it. Returns a 'pahandle' device  
handle for the device. All parameters are optional and have reasonable defaults.  
'deviceid' Index to select amongst multiple logical audio devices supported by  
[PortAudio](PortAudio). Defaults to whatever the systems default sound device is. Different  
device id's may select the same physical device, but controlled by a different  
low-level sound system. E.g., Windows has about five different sound subsystems.  
'mode' Mode of operation. Defaults to 1 == sound playback only. Can be set to 2  
== audio capture, or 3 for simultaneous capture and playback of sound. Note  
however that mode 3 (full duplex) does not work reliably on all sound hardware.  
On some hardware this mode may crash Matlab! There is also a special monitoring  
mode == 7, which only works for full duplex devices when using the same number  
of input- and outputchannels. This mode allows direct feedback of captured  
sounds back to the speakers with minimal latency and without involvement of your  
script at all, however no sound can be captured during this time and your code  
mostly doesn't have any control over timing etc.   
You can also define a audio device as a master device by adding the value 8 to  
mode. Master devices themselves are not directly used to playback or capture  
sound. Instead one can create (multiple) slave devices that are attached to a  
master device. Each slave can be controlled independently to playback or record  
sound through a subset of the channels of the master device. This basically  
allows to virtualize a soundcard. See help for subfunction 'OpenSlave' for more  
info.  
'reqlatencyclass' Allows to select how aggressive [PsychPortAudio](PsychPortAudio) should be about  
minimizing sound latency and getting good deterministic timing, i.e. how to  
trade off latency vs. system load and playing nicely with other sound  
applications on the system. Level 0 means: Don't care about latency, this mode  
works always and with all settings, plays nicely with other sound applications.  
Level 1 (the default) means: Try to get the lowest latency that is possible  
under the constraint of reliable playback, freedom of choice for all parameters  
and interoperability with other applications. Level 2 means: Take full control  
over the audio device, even if this causes other sound applications to fail or  
shutdown. Level 3 means: As level 2, but request the most aggressive settings  
for the given device. Level 4: Same as 3, but fail if device can't meet the  
strictest requirements. 'freq' Requested playback/capture rate in samples per  
second (Hz). Defaults to a value that depends on the requested latency mode.  
'channels' Number of audio channels to use, defaults to 2 for stereo. If you  
perform simultaneous playback and recording, you can provide a 2 element vector  
for 'channels', specifying different numbers of output channels and input  
channels. The first element in such a vector defines the number of playback  
channels, the 2nd element defines capture channels. E.g., [2, 1] would define 2  
playback channels (stereo) and 1 recording channel. See the optional  
'selectchannels' argument for selection of physical device channels on multi-  
channel cards.  
'buffersize' requested size and number of internal audio buffers, smaller  
numbers mean lower latency but higher system load and some risk of overloading,  
which would cause audio dropouts. 'suggestedLatency' optional requested latency  
in seconds. [PortAudio](PortAudio) selects internal operating parameters depending on  
sampleRate, suggestedLatency and buffersize as well as device internal  
properties to optimize for low latency output. Best left alone, only here as  
manual override in case all the auto-tuning cleverness fails.  
 'selectchannels' optional matrix with mappings of logical channels to device  
channels: If you only want to use a subset of the channels present on your sound  
card, e.g., only 2 playback channels on a 16 channel soundcard, then you'd set  
the 'channels' argument to 2. The 'selectchannels' argument allows you to  
select, e.g.,  which two of the 16 channels to use for playback.  
'selectchannels' is a one row by 'channels' matrix with mappings for pure  
playback or pure capture. For full-duplex mode (playback and capture),  
'selectchannels' must be a 2 rows by max(channels) column matrix. row 1 will  
define playback channel mappings, whereas row 2 will then define capture channel  
mappings. In any case, the number in the i'th column will define which physical  
device channel will be used for playback or capture of the i'th [PsychPortAudio](PsychPortAudio)  
channel (the i'th row of your sound matrix). Numbering of physical device  
channels starts with zero! Example: Both, playback and simultaneous recording  
are requested and 'channels' equals 2, ie, two playback channels and two capture  
channels. If you'd specify 'selectchannels' as [0, 6 ; 12, 14], then playback  
would happen to device channels zero and six, sound would be captured from  
device channels 12 and 14. Please note that channel selection is currently only  
supported on MS-Windows with ASIO sound cards. The parameter is silently ignored  
for non-ASIO operation.  
  
'specialFlags' Optional flags: Default to zero, can be or'ed or added together  
with the following flags/settings:  
1 = Never prime output stream. By default the output stream is primed. Don't  
bother if you don't know what this means.  
2 = Always clamp audio data to the valid -1.0 to 1.0 range. Clamping is enabled  
by default.  
4 = Never clamp audio data.  
8 = Always dither output audio data. By default, dithering is enabled in normal  
mode, and disabled in low-latency mode. Dithering adds a stochastic noise  
pattern to the least significant bit of each output sample to reduce the impact  
of audio quantization artifacts. Dithering can improve signal to noise ratio and  
quality of output sound, but it is more compute intense and it could change very  
low-level properties of the audio signal, because what you hear is not exactly  
what you specified.  
16 = Never dither audio data, not even in normal mode.  
  
  


###See also:
Close [GetDeviceSettings](PsychPortAudio-GetDeviceSettings) 
