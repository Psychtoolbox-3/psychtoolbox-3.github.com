# [PsychPortAudio](PsychPortAudio)
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio)

PsychPortAudio - A sound driver built around the PortAudio sound library:  
  
  
General information:  
  
version = PsychPortAudio('[Version](PsychPortAudio-Version)');  
oldlevel = PsychPortAudio('[Verbosity](PsychPortAudio-Verbosity)' [,level]);  
count = PsychPortAudio('[GetOpenDeviceCount](PsychPortAudio-GetOpenDeviceCount)');  
devices = PsychPortAudio('[GetDevices](PsychPortAudio-GetDevices)' [,devicetype] [, deviceIndex]);  
  
General settings:  
  
[oldyieldInterval, oldMutexEnable, lockToCore1, audioserver_autosuspend] = PsychPortAudio('[EngineTunables](PsychPortAudio-EngineTunables)' [, yieldInterval] [, MutexEnable] [, lockToCore1] [, audioserver_autosuspend]);  
oldRunMode = PsychPortAudio('[RunMode](PsychPortAudio-RunMode)', pahandle [,runMode]);  
  
  
Device setup and shutdown:  
  
pahandle = PsychPortAudio('[Open](PsychPortAudio-Open)' [, deviceid][, mode][, reqlatencyclass][, freq][, channels][, buffersize][, suggestedLatency][, selectchannels][, specialFlags=0]);  
pahandle = PsychPortAudio('[OpenSlave](PsychPortAudio-OpenSlave)', pamaster [, mode][, channels][, selectchannels]);  
PsychPortAudio('[Close](PsychPortAudio-Close)' [, pahandle]);  
oldOpMode = PsychPortAudio('[SetOpMode](PsychPortAudio-SetOpMode)', pahandle [, opModeOverride]);  
oldbias = PsychPortAudio('[LatencyBias](PsychPortAudio-LatencyBias)', pahandle [,biasSecs]);  
[oldMasterVolume, oldChannelVolumes] = PsychPortAudio('[Volume](PsychPortAudio-Volume)', pahandle [, masterVolume][, channelVolumes]);  
enable = PsychPortAudio('[DirectInputMonitoring](PsychPortAudio-DirectInputMonitoring)', pahandle, enable [, inputChannel = -1][, outputChannel = 0][, gainLevel = 0.0][, stereoPan = 0.5]);  
[underflow, nextSampleStartIndex, nextSampleETASecs] = PsychPortAudio('[FillBuffer](PsychPortAudio-FillBuffer)', pahandle, bufferdata [, streamingrefill=0][, startIndex=Append]);  
bufferhandle = PsychPortAudio('[CreateBuffer](PsychPortAudio-CreateBuffer)' [, pahandle], bufferdata);  
PsychPortAudio('[DeleteBuffer](PsychPortAudio-DeleteBuffer)'[, bufferhandle] [, waitmode]);  
PsychPortAudio('[RefillBuffer](PsychPortAudio-RefillBuffer)', pahandle [, bufferhandle=0], bufferdata [, startIndex=0]);  
PsychPortAudio('[SetLoop](PsychPortAudio-SetLoop)', pahandle[, startSample=0][, endSample=max][, UnitIsSeconds=0]);  
startTime = PsychPortAudio('[Start](PsychPortAudio-Start)', pahandle [, repetitions=1] [, when=0] [, waitForStart=0] [, stopTime=inf] [, resume=0]);  
startTime = PsychPortAudio('[RescheduleStart](PsychPortAudio-RescheduleStart)', pahandle, when [, waitForStart=0] [, repetitions] [, stopTime]);  
status = PsychPortAudio('[GetStatus](PsychPortAudio-GetStatus)' pahandle);  
[audiodata absrecposition overflow cstarttime] = PsychPortAudio('[GetAudioData](PsychPortAudio-GetAudioData)', pahandle [, amountToAllocateSecs][, minimumAmountToReturnSecs][, maximumAmountToReturnSecs][, singleType=0]);  
[startTime endPositionSecs xruns estStopTime] = PsychPortAudio('[Stop](PsychPortAudio-Stop)', pahandle [,waitForEndOfPlayback=0] [, blockUntilStopped=1] [, repetitions] [, stopTime]);  
PsychPortAudio('[UseSchedule](PsychPortAudio-UseSchedule)', pahandle, enableSchedule [, maxSize = 128]);  
[success, freeslots] = PsychPortAudio('[AddToSchedule](PsychPortAudio-AddToSchedule)', pahandle [, bufferHandle=0][, repetitions=1][, startSample=0][, endSample=max][, UnitIsSeconds=0][, specialFlags=0]);  
  

  [PsychPortAudio](PsychPortAudio) - High precision sound driver for Psychtoolbox-3.  
   
  [PsychPortAudio](PsychPortAudio) is a special sounddriver for PTB-3. It is a replacement  
  for all other Matlab based sound drivers and PTB's old SND() function.  
   
  [PsychPortAudio](PsychPortAudio) provides the following features:  
   
  - Allows instant start of sound playback with a very low onset latency  
    compared to other sound drivers (on well working hardware).  
   
  - Allows start of playback at a scheduled future system time: E.g.,  
    schedule sound onset for a specific time in the future (e.g., visual  
    stimulus onset time), then do other things in your Matlab code.  
    Scheduled start of playback can be accurate to the sub-millisecond level  
    on some system setups.  
   
  - Wait for sound onset, or continue with execution of your code  
    immediately.  
   
  - Asynchronous operation: Sound playback works in the background while  
    your code continues to do other things.  
   
  - Infinitely repeating playback, or playback of a sound for 'n' times.  
   
  - Returns timestamps and status for all crucial events.  
   
  - Support multi-channel devices, e.g., 8-channel sound cards.  
   
  - Supports multi-channel sound capture and full-duplex capture  
    and playback of sound on some systems.  
   
  - Enumerate, open and use multiple sound cards in parallel.  
   
  - Reliable (compared to Matlabs sound facilities).  
   
  - Efficient, causes only very low cpu load.  
   
  See the "help [InitializePsychSound](InitializePsychSound)" for more info on low-latency  
  configurations. See "help [BasicSoundOutputDemo](BasicSoundOutputDemo)" for a very basic demo of  
  sound output (without special emphasis on low-latency). See  
  "[BasicSoundInputDemo](BasicSoundInputDemo)" for a basic demo of sound capture.  
  "[BasicSoundFeedbackDemo](BasicSoundFeedbackDemo)" shows how to implement a simple audio feedback  
  loop with controllable delay.  
   
  "[PsychPortAudioTimingTest](PsychPortAudioTimingTest)" is a script that we used for testing PA's  
  sound onset latency and accuracy. It also serves as an example on how to  
  get perfectly synched audio-visual stimulus onsets.  
   
  Type "[PsychPortAudio](PsychPortAudio)" for an overview of supported subfunctions and  
  "[PsychPortAudio](PsychPortAudio) Subfunctionname?" for help on a specific subfunction.  
   
  CAUTION: You \*must\* call [InitializePsychSound](InitializePsychSound) before first invocation of  
  [PsychPortAudio](PsychPortAudio)(), at least on MS-Windows, but possibly also on OS/X! If  
  you omit that call, initialization of the driver may fail with some  
  "Invalid MEX file" error from Matlab!  
   
   
  [PsychPortAudio](PsychPortAudio) is built around a modified version of the free, open-source  
  [PortAudio](PortAudio) sound library for portable realtime sound: http://www.portaudio.com  
  


