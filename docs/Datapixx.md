# [Datapixx](Datapixx)
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx)

Usage:  
  
% Setup functions:  
isReady = Datapixx('[Open](Datapixx-Open)');  
isReady = Datapixx('[IsReady](Datapixx-IsReady)');  
isDatapixx = Datapixx('[IsDatapixx](Datapixx-IsDatapixx)');  
isDatapixx2 = Datapixx('[IsDatapixx2](Datapixx-IsDatapixx2)');  
isViewpixx = Datapixx('[IsViewpixx](Datapixx-IsViewpixx)');  
isViewpixx3D = Datapixx('[IsViewpixx3D](Datapixx-IsViewpixx3D)');  
isPropixxCtrl = Datapixx('[IsPropixxCtrl](Datapixx-IsPropixxCtrl)');  
isPropixx = Datapixx('[IsPropixx](Datapixx-IsPropixx)');  
Datapixx('[Close](Datapixx-Close)');  
  
% Global system information:  
ramSize = Datapixx('[GetRamSize](Datapixx-GetRamSize)');  
firmwareRev = Datapixx('[GetFirmwareRev](Datapixx-GetFirmwareRev)');  
time = Datapixx('[GetTime](Datapixx-GetTime)');  
Datapixx('[SetMarker](Datapixx-SetMarker)');  
marker = Datapixx('[GetMarker](Datapixx-GetMarker)');  
supplyVoltage = Datapixx('[GetSupplyVoltage](Datapixx-GetSupplyVoltage)');  
supplyCurrent = Datapixx('[GetSupplyCurrent](Datapixx-GetSupplyCurrent)');  
is5VFault = Datapixx('[Is5VFault](Datapixx-Is5VFault)');  
tempCelcius = Datapixx('[GetTempCelcius](Datapixx-GetTempCelcius)');  
tempFarenheit = Datapixx('[GetTempFarenheit](Datapixx-GetTempFarenheit)');  
  
% DAC (Digital to Analog Converter) subsystem:  
dacNumChannels = Datapixx('[GetDacNumChannels](Datapixx-GetDacNumChannels)');  
dacRanges = Datapixx('[GetDacRanges](Datapixx-GetDacRanges)');  
Datapixx('[SetDacVoltages](Datapixx-SetDacVoltages)', channelVoltagePairs);  
dacVoltages = Datapixx('[GetDacVoltages](Datapixx-GetDacVoltages)');  
[nextBufferAddress, underflow, overflow] = Datapixx('[WriteDacBuffer](Datapixx-WriteDacBuffer)', bufferData [, bufferAddress=0] [, channelList=[0:numChannels-1]]);  
Datapixx('[SetDacSchedule](Datapixx-SetDacSchedule)', scheduleOnset, scheduleRate, maxScheduleFrames [, channelList=0] [, bufferBaseAddress=0] [, numBufferFrames=maxScheduleFrames]);  
Datapixx('[StartDacSchedule](Datapixx-StartDacSchedule)');  
Datapixx('[StopDacSchedule](Datapixx-StopDacSchedule)');  
status = Datapixx('[GetDacStatus](Datapixx-GetDacStatus)');  
  
% ADC (Analog to Digital Converter) subsystem:  
adcNumChannels = Datapixx('[GetAdcNumChannels](Datapixx-GetAdcNumChannels)');  
adcRanges = Datapixx('[GetAdcRanges](Datapixx-GetAdcRanges)');  
adcVoltages = Datapixx('[GetAdcVoltages](Datapixx-GetAdcVoltages)');  
Datapixx('[EnableDacAdcLoopback](Datapixx-EnableDacAdcLoopback)');  
Datapixx('[DisableDacAdcLoopback](Datapixx-DisableDacAdcLoopback)');  
Datapixx('[EnableAdcFreeRunning](Datapixx-EnableAdcFreeRunning)');  
Datapixx('[DisableAdcFreeRunning](Datapixx-DisableAdcFreeRunning)');  
Datapixx('[SetAdcSchedule](Datapixx-SetAdcSchedule)', scheduleOnset, scheduleRate, maxScheduleFrames [, channelList=0] [, bufferBaseAddress=4e6] [, numBufferFrames=maxScheduleFrames]);  
Datapixx('[StartAdcSchedule](Datapixx-StartAdcSchedule)');  
Datapixx('[StopAdcSchedule](Datapixx-StopAdcSchedule)');  
[bufferData, bufferTimetags, underflow, overflow] = Datapixx('[ReadAdcBuffer](Datapixx-ReadAdcBuffer)', numFrames [, bufferAddress]);  
status = Datapixx('[GetAdcStatus](Datapixx-GetAdcStatus)');  
  
% DOUT (Digital Output) subsystem:  
doutNumBits = Datapixx('[GetDoutNumBits](Datapixx-GetDoutNumBits)');  
Datapixx('[SetDoutValues](Datapixx-SetDoutValues)', bitValues [, bitMask = 0x00FFFFFF])  
doutValues = Datapixx('[GetDoutValues](Datapixx-GetDoutValues)');  
Datapixx('[EnableDoutButtonSchedules](Datapixx-EnableDoutButtonSchedules)');  
Datapixx('[DisableDoutButtonSchedules](Datapixx-DisableDoutButtonSchedules)');  
Datapixx('[EnableDoutBacklightPulse](Datapixx-EnableDoutBacklightPulse)');  
Datapixx('[DisableDoutBacklightPulse](Datapixx-DisableDoutBacklightPulse)');  
[nextBufferAddress, underflow, overflow] = Datapixx('[WriteDoutBuffer](Datapixx-WriteDoutBuffer)', bufferData [, bufferAddress=8e6]);  
Datapixx('[SetDoutSchedule](Datapixx-SetDoutSchedule)', scheduleOnset, scheduleRate, maxScheduleFrames [, bufferBaseAddress=8e6] [, numBufferFrames=maxScheduleFrames]);  
Datapixx('[StartDoutSchedule](Datapixx-StartDoutSchedule)');  
Datapixx('[StopDoutSchedule](Datapixx-StopDoutSchedule)');  
status = Datapixx('[GetDoutStatus](Datapixx-GetDoutStatus)');  
  
% DIN (Digital Input) subsystem:  
dinNumBits = Datapixx('[GetDinNumBits](Datapixx-GetDinNumBits)');  
dinValues = Datapixx('[GetDinValues](Datapixx-GetDinValues)');  
Datapixx('[SetDinDataDirection](Datapixx-SetDinDataDirection)', directionMask);  
Datapixx('[SetDinDataOut](Datapixx-SetDinDataOut)', dataOut);  
doutValues = Datapixx('[GetDinDataOut](Datapixx-GetDinDataOut)');  
Datapixx('[SetDinDataOutStrength](Datapixx-SetDinDataOutStrength)', strength);  
Datapixx('[EnableDinDebounce](Datapixx-EnableDinDebounce)');  
Datapixx('[DisableDinDebounce](Datapixx-DisableDinDebounce)');  
Datapixx('[EnableDoutDinLoopback](Datapixx-EnableDoutDinLoopback)');  
Datapixx('[DisableDoutDinLoopback](Datapixx-DisableDoutDinLoopback)');  
Datapixx('[SetDinLog](Datapixx-SetDinLog)' [, bufferBaseAddress=12e6] [, numBufferFrames=1000]);  
Datapixx('[StartDinLog](Datapixx-StartDinLog)');  
Datapixx('[StopDinLog](Datapixx-StopDinLog)');  
[logData, logTimetags, underflow] = Datapixx('[ReadDinLog](Datapixx-ReadDinLog)' [, numFrames]);  
status = Datapixx('[GetDinStatus](Datapixx-GetDinStatus)');  
  
% TOUCHPixx (touch panel) subsystem:  
Datapixx('[EnableTouchpixx](Datapixx-EnableTouchpixx)');  
Datapixx('[DisableTouchpixx](Datapixx-DisableTouchpixx)');  
coordinates = Datapixx('[GetTouchpixxCoordinates](Datapixx-GetTouchpixxCoordinates)');  
Datapixx('[SetTouchpixxStabilizeDuration](Datapixx-SetTouchpixxStabilizeDuration)', duration);  
Datapixx('[SetTouchpixxLog](Datapixx-SetTouchpixxLog)' [, bufferBaseAddress=12e6] [, numBufferFrames=1000]);  
Datapixx('[StartTouchpixxLog](Datapixx-StartTouchpixxLog)');  
Datapixx('[StopTouchpixxLog](Datapixx-StopTouchpixxLog)');  
[logCoords, logTimetags, underflow] = Datapixx('[ReadTouchpixxLog](Datapixx-ReadTouchpixxLog)' [, numFrames]);  
Datapixx('[EnableTouchpixxLogContinuousMode](Datapixx-EnableTouchpixxLogContinuousMode)');  
Datapixx('[DisableTouchpixxLogContinuousMode](Datapixx-DisableTouchpixxLogContinuousMode)');  
status = Datapixx('[GetTouchpixxStatus](Datapixx-GetTouchpixxStatus)');  
  
% Audio Output subsystem:  
Datapixx('[InitAudio](Datapixx-InitAudio)');  
Datapixx('[SetAudioVolume](Datapixx-SetAudioVolume)', volume);  
[nextBufferAddress, underflow, overflow] = Datapixx('[WriteAudioBuffer](Datapixx-WriteAudioBuffer)', bufferData [, bufferAddress=16e6]);  
delay = Datapixx('[GetAudioGroupDelay](Datapixx-GetAudioGroupDelay)', sampleRate);  
Datapixx('[SetAudioSchedule](Datapixx-SetAudioSchedule)', scheduleOnset, scheduleRate, maxScheduleFrames [, lrMode=mono] [, bufferBaseAddress=16e6] [, numBufferFrames=maxScheduleFrames]);  
Datapixx('[StartAudioSchedule](Datapixx-StartAudioSchedule)');  
Datapixx('[StopAudioSchedule](Datapixx-StopAudioSchedule)');  
status = Datapixx('[GetAudioStatus](Datapixx-GetAudioStatus)');  
  
% Microphone input subsystem:  
Datapixx('[SetMicrophoneSource](Datapixx-SetMicrophoneSource)', source [, gain]);  
Datapixx('[EnableAudioLoopback](Datapixx-EnableAudioLoopback)');  
Datapixx('[DisableAudioLoopback](Datapixx-DisableAudioLoopback)');  
delay = Datapixx('[GetMicrophoneGroupDelay](Datapixx-GetMicrophoneGroupDelay)', sampleRate);  
Datapixx('[SetMicrophoneSchedule](Datapixx-SetMicrophoneSchedule)', scheduleOnset, scheduleRate, maxScheduleFrames [, lrMode=mono] [, bufferBaseAddress=20e6] [, numBufferFrames=maxScheduleFrames]);  
Datapixx('[StartMicrophoneSchedule](Datapixx-StartMicrophoneSchedule)');  
Datapixx('[StopMicrophoneSchedule](Datapixx-StopMicrophoneSchedule)');  
[bufferData, underflow, overflow] = Datapixx('[ReadMicrophoneBuffer](Datapixx-ReadMicrophoneBuffer)', numFrames [, bufferAddress]);  
status = Datapixx('[GetMicrophoneStatus](Datapixx-GetMicrophoneStatus)');  
  
% Video subsystem:  
Datapixx('[SetVideoMode](Datapixx-SetVideoMode)' [, mode=0]);  
Datapixx('[SetVideoClut](Datapixx-SetVideoClut)', clut);  
Datapixx('[SetVideoHorizontalSplit](Datapixx-SetVideoHorizontalSplit)', mode(0=MIRROR,1=SPLIT,2=AUTO));  
Datapixx('[SetVideoVerticalStereo](Datapixx-SetVideoVerticalStereo)', mode(0=NO_STEREO,1=STEREO,2=AUTO));  
Datapixx('[SetVideoStereoEye](Datapixx-SetVideoStereoEye)', eye(1=Left,0=Right));  
Datapixx('[EnableVideoStereoBlueline](Datapixx-EnableVideoStereoBlueline)');  
Datapixx('[DisableVideoStereoBlueline](Datapixx-DisableVideoStereoBlueline)');  
Datapixx('[SetVideoStereoVesaWaveform](Datapixx-SetVideoStereoVesaWaveform)', waveform);  
Datapixx('[EnableVideoHorizontalOverlay](Datapixx-EnableVideoHorizontalOverlay)');  
Datapixx('[DisableVideoHorizontalOverlay](Datapixx-DisableVideoHorizontalOverlay)');  
Datapixx('[SetVideoHorizontalOverlayBounds](Datapixx-SetVideoHorizontalOverlayBounds)', boundsRect);  
Datapixx('[SetVideoHorizontalOverlayAlpha](Datapixx-SetVideoHorizontalOverlayAlpha)', alphaTable);  
Datapixx('[SetVideoPixelSyncLine](Datapixx-SetVideoPixelSyncLine)', rasterLine [, singleLine=1] [, blankLine=1]);  
Datapixx('[EnableVideoScanningBacklight](Datapixx-EnableVideoScanningBacklight)');  
Datapixx('[DisableVideoScanningBacklight](Datapixx-DisableVideoScanningBacklight)');  
Datapixx('[EnableVideoLcd3D60Hz](Datapixx-EnableVideoLcd3D60Hz)');  
Datapixx('[DisableVideoLcd3D60Hz](Datapixx-DisableVideoLcd3D60Hz)');  
pixels = Datapixx('[GetVideoLine](Datapixx-GetVideoLine)' [, nPixels=HORIZONTAL_RESOLUTION]);  
status = Datapixx('[GetVideoStatus](Datapixx-GetVideoStatus)');  
  
% PROPixx-specific routines:  
Datapixx('[SetPropixxDlpSequenceProgram](Datapixx-SetPropixxDlpSequenceProgram)' [, program=0]);  
Datapixx('[EnablePropixxCeilingMount](Datapixx-EnablePropixxCeilingMount)');  
Datapixx('[DisablePropixxCeilingMount](Datapixx-DisablePropixxCeilingMount)');  
Datapixx('[EnablePropixxRearProjection](Datapixx-EnablePropixxRearProjection)');  
Datapixx('[DisablePropixxRearProjection](Datapixx-DisablePropixxRearProjection)');  
Datapixx('[SetPropixx3DCrosstalk](Datapixx-SetPropixx3DCrosstalk)', crosstalk);  
Datapixx('[SetPropixx3DCrosstalkLR](Datapixx-SetPropixx3DCrosstalkLR)', crosstalk);  
Datapixx('[SetPropixx3DCrosstalkRL](Datapixx-SetPropixx3DCrosstalkRL)', crosstalk);  
  
% Reading and writing register cache:  
Datapixx('[RegWr](Datapixx-RegWr)');  
Datapixx('[RegWrRd](Datapixx-RegWrRd)');  
Datapixx('[RegWrVideoSync](Datapixx-RegWrVideoSync)');  
Datapixx('[RegWrRdVideoSync](Datapixx-RegWrRdVideoSync)');  
Datapixx('[RegWrPixelSync](Datapixx-RegWrPixelSync)', pixelSequence [, timeout=255]);  
isTimeout = Datapixx('RegWrRdPixelSync, pixelSequence [, timeout=255]);  
  
% Miscellaneous Routines:  
Datapixx('[StopAllSchedules](Datapixx-StopAllSchedules)');  
error = Datapixx('[GetError](Datapixx-GetError)');  
Datapixx('[ClearError](Datapixx-ClearError)');  
Datapixx('[Reset](Datapixx-Reset)');  
  

 Datapixx is a MEX file for precise control of the [DataPixx](DataPixx) device from  
 [VPixx](VPixx) Technologies. It has many functions; type "Datapixx" for a list:  
    Datapixx  
  
 For explanation of any particular Datapixx function, just add a question  
 mark "?". E.g. for 'Open', try either of these equivalent forms:  
    Datapixx('Open?')  
    Datapixx Open?  
  
 Most of the time you won't use this function directly, but instead use  
 the [PsychDataPixx](PsychDataPixx)() function for more convenient control and execution of  
 common tasks.  
  
 For setup of Datapixx video operations, check the online help of  
 [PsychImaging](PsychImaging)(), which has multiple functions for interacting with the  
 Datapixx device.  
  
 For an overview of demos and other useful helper functions for the [DataPixx](DataPixx),  
 type "help [DatapixxToolbox](DatapixxToolbox)".  
  
  
  


