# [PsychPortAudio('OpenSlave')](PsychPortAudio-OpenSlave) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction

pahandle = PsychPortAudio('OpenSlave', pamaster [, mode][, channels][, selectchannels]);

Open a virtual slave audio device and initialize it. Returns a 'pahandle' device  
handle for the device.  
Slave audio devices are almost always attached to a 'pamaster' audio device that  
you need to open and initialize first via a call to pamaster =  
[PsychPortAudio](PsychPortAudio)('Open', ...); The 'pamaster' corresponds to a real soundcard  
present in your system which has been setup for a certain mode of operation,  
timing mode, frequency etc. The exception is if you create an [AMModulator](AMModulator) slave  
(see below). It can be attached to another playback slave device by passing the  
handle of that device as 'pamaster'. To each real pamaster you can attach  
multiple slave devices. Each slave represents a subset of the audio channels of  
the pamaster device. Each slave can be used as if it is a real independent  
soundcard for capture or playback with or without its own set of playback  
buffers, its own schedule and mode of operation, its own start and stop times,  
status etc. Under the hood, the slave device will use the defined subset of  
channels of the master device to achieve this illusion of independent  
soundcards. Typical usage scenarios would be:  
  
\* Mixing of independent soundtracks: Create multiple slave devices, one for each  
soundtrack. Attach all of them to the same set of channels on a common master  
device. Now you can feed each slave with its own soundtrack, start, stop and  
schedule playback of each slave/soundtrack independently. Sound from all active  
channels of all active slaves will be mixed together and output through the  
channels of the master device.  
  
\* Independent control of channels: Same as above, but the slaves don't share the  
same subset of channels on the master, but each slave chooses a distinctive  
subset of channels, therefore no mixing will occur.  
  
'pamaster' is the mandatory pahandle of a master audio device. The master must  
have been opened via [PsychPortAudio](PsychPortAudio)('Open', ..., mode, ...); with the mode flag  
value '8' included to define it as a master (see 'Open').  
  
'mode' Mode of operation. See help of 'Open' function for valid settings.  
However, a mode flag of '8' for master operation is not allowed for obvious  
reasons. Also, the given 'mode' flags must be a subset of the 'mode' set on the  
master device! E.g., you can't specify a audio capture mode flag if the master  
device isn't enabled for capture as well. As an exception kPortAudioMonitoring  
mode is allowed to be present on a slave while missing on the associated master  
device.  
The slave-only mode flag 32 (kPortAudioIsAMModulator) defines a slave device not  
as a source of audio data, but as a source of amplitude modulation (AM) envelope  
data. Its samples don't create sound, but gain-modulate the sound of other  
slaves attached to the master to allow precisely timed AM modulation. See the  
help for [PsychPortAudio](PsychPortAudio)('Volume') for more details about AM.  
  
The slave-only mode flag 64 (kPortAudioIsOutputCapture) defines a slave capture  
device that captures audio data from the \*output channels\* of the master device,  
i.e., it records the audio stream that is sent to the speakers. This may be  
useful for capturing PsychPortAudio's audio output for documentation or debug  
purposes.  
  
All slave devices share the same settings for latencymode, timing, sampling  
frequency and other low-level tunable parameters, because they operate on the  
same underlying audio hardware.  
  
'channels' Define total number of playback and capture channels to use. See help  
for 'Open?' for explanation. By default, all channels of the master are used.  
  
'selectchannels' optional matrix with mappings of logical slave channels to  
logical master channels: selectchannels' is a one row by 'channels' matrix with  
mappings for pure playback or pure capture. For full-duplex mode (playback and  
capture), 'selectchannels' must be a 2 rows by max(channels) column matrix. row  
1 will define playback channel mappings, whereas row 2 will then define capture  
channel mappings. In any case, the number in the i'th column will define which  
master device channel will be used for playback or capture of the i'th  
[PsychPortAudio](PsychPortAudio) channel (the i'th row of your sound matrix). Numbering of master  
device channels starts with one! Example: Both, playback and simultaneous  
recording are requested from a master device which represents a 16 channel  
soundcard with all 16 channels open. If you'd specify 'selectchannels' as [1, 6  
; 12, 14], then playback would happen to master channels one and six, sound  
would be captured from master channels 12 and 14.  
  
  


###See also:
Open Close [GetDeviceSettings](PsychPortAudio-GetDeviceSettings) 
