# [PsychPortAudio('Volume')](PsychPortAudio-Volume) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction

[oldMasterVolume, oldChannelVolumes] = PsychPortAudio('Volume', pahandle [, masterVolume][, channelVolumes]);

Set audio output volume(s) and/or return old volumes for a device 'pahandle'.  
The device must be open for this setting to take effect. It is initially set to  
1.0. On a regular audio device or master device, you can only set the global  
'masterVolume' for the whole device. On a slave device, you can optionally  
define a per-channel volume vector 'channelVolumes'. E.g., if your slave device  
has two output channels, a 'channelVolumes' vector of [0.9 ; 0.25] would set the  
first channel to 90% intensity, the 2nd channel to 25% intensity. The elements  
of 'channelVolumes' and the 'masterVolume' can be any value. The value for a  
device or a channel is simply multiplied with each output sample before output  
to the hardware, so that a value of 1.0 (the default setting for each device and  
channel) will pass samples unmodified, a value of 0.5 would reduce intensity to  
50%, a value of 1.25 would amplify to 125% of the original value, or a value of  
-1 would invert the signal.  
Be careful with amplification (values \> 1). If the final sample leaves the valid  
output range of -1.0 to 1.0, you may hear ugly auditory clipping artifacts and  
possibly damage your ears or speakers! In 'normal' mode, [PsychPortAudio](PsychPortAudio) clamps  
output samples to the valid range of -1 to 1, but in high timing precision/low  
latency mode, clamping is not performed in order to save computation time.  
  
Caution: All volume settings are silently ignored on regular audio devices or  
master devices if audio monitoring mode is active. On a slave device,  
per-channel volumes would be still applied in monitoring mode, but not the  
masterVolume. This is for efficiency reasons. If you need volume settings in  
monitoring mode, then open a master device, attach a slave device to it in  
monitoring mode, then set the 'channelVolumes' of that slave device to control  
volume of monitoring.  
  
Caution: The volume settings only affect what is sent to your computers sound  
system. The operating system or audio hardware itself may apply additional  
volume settings, gains, filters etc., depending on your specific setup. These  
are only controllable via external system specific tools, [PsychPortAudio](PsychPortAudio) doesn't  
know about such additional settings and can't control them in any way!  
  
If you need to modulate output volume over time, you can also attach an  
additional slave device whose opMode is set to act as an [AMmodulator](AMmodulator) to a master  
or slave device, see help for 'OpenSlave'. Such a slave device will not output  
sound itself, but use the data stored in its playback buffers to modulate the  
amplitude of its parent slave, or of the summed signal of all previously  
attached slaves for a master over time. Example: You create a master device,  
then 'OpenSlave' three regular slave devices, then 'OpenSlave' a [AMmodulator](AMmodulator)  
slave device. During playback, the sound signals of the three regular slaves  
will be mixed together. The combined signal will be multiplied by the per-sample  
volume values provided by the [AMmodulator](AMmodulator) slave device, thereby modulating the  
amplitude or ''acoustic envelope'' of the mixed signals. The resulting signal  
will be played by the master device. If you'd attach more regular slave devices  
after the [AMmodulator](AMmodulator), their signal would not get modulated, but simply added to  
the modulated signal of the first three devices.  
  
You can also modulate only the signals of a specific slave device, by attaching  
the modulator to that slave device in the 'OpenSlave' call. You'd simply pass  
the handle of the slave that should be modulated to 'OpenSlave', instead of the  
handle of a master device.  
  
  


###See also:
Open 
