# [PsychPortAudio('EngineTunables')](PsychPortAudio-EngineTunables) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction

[oldyieldInterval, oldMutexEnable, lockToCore1, audioserver_autosuspend] = PsychPortAudio('EngineTunables' [, yieldInterval] [, MutexEnable] [, lockToCore1] [, audioserver_autosuspend]);

Return, and optionally set low-level tuneable driver parameters.  
The driver must be idle, ie., no audio device must be open, if you want to  
change tuneables! These tuneable parameters usually have reasonably chosen  
defaults and you should only need to change them to work around bugs or flaws in  
your operating system, sound hardware or drivers, or if you have very unusual  
needs or setups. Only touch these if you know what you're doing, probably after  
consultation with the Psychtoolbox forum or Wiki. Some of these have potential  
to cause serious system malfunctions if not selected properly!  
  
'yieldInterval' - If the driver has to perform polling operations, it will  
release the cpu for yieldInterval seconds inbetween unsuccessful polling  
iterations. Valid range is 0.0 to 0.1 secs, with a reasonable default of 0.001  
secs ie. 1 msec.  
'MutexEnable' - Enable (1) or Disable (0) internal mutex locking of driver data  
structures to prevent potential race-conditions between internal processing  
threads. Locking is enabled by default. Only disable locking to work around  
seriously broken audio device drivers or system setups and be aware that this  
may have unpleasant side effects and can cause all kinds of malfunctions by  
itself!  
'lockToCore1' - Deprecated: Enable (1) or Disable (0) locking of all audio  
engine processing threads to cpu core 1 on Microsoft Windows systems. By default  
threads are locked to cpu core 1 to avoid problems with timestamping due to bugs  
in some microprocessors clocks and in Microsoft Windows itself. If you're  
confident/certain that your system is bugfree wrt. to its clocks and want to get  
a bit more performance out of multi-core machines, you can disable this. You  
must perform this setting before you open the first audio device the first time,  
otherwise the setting might be ignored. In the current driver this setting is  
silently ignored, as a new method of handling this has been implemented.  
'audioserver\_autosuspend' - Enable (1) or Disable (0) automatic suspending of  
running desktop audio servers, e.g., [PulseAudio](PulseAudio), while [PsychPortAudio](PsychPortAudio) is active.  
Default is (1) - suspend while [PsychPortAudio](PsychPortAudio) does its thing. Desktop sound  
servers like the commonly used [PulseAudio](PulseAudio) server can interfere with low level  
audio device access and low-latency / high-precision audio timing. For this  
reason it is a good idea to switch them to standby (suspend) while a  
[PsychPortAudio](PsychPortAudio) session is active. Sometimes this isn't needed or not even  
desireable. Therefore this option allows to inhibit this automatic suspending of  
audio servers.  
  


###See also:
Open 
