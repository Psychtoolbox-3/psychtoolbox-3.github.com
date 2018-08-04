# [Screen('Preference')](Screen-Preference) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Get or set a Psychtoolbox preference.[Preference](Preference) settings are global - they  
affect all operations of a module until changed.  
oldBool = [Screen](Screen)('[Preference](Preference)', 'IgnoreCase', [psych\_bool]);  
tick0Secs = [Screen](Screen)('[Preference](Preference)', 'Tick0Secs', tick0Secs);  
psychTableVersion = [Screen](Screen)('[Preference](Preference)', 'PsychTableVersion');  
mexFunctionName = [Screen](Screen)('[Preference](Preference)', 'PsychTableCreator');  
proc = [Screen](Screen)('[Preference](Preference)', 'Process', signature);  
proc = [Screen](Screen)('[Preference](Preference)', 'DebugMakeTexture', enableDebugging);  
oldEnableFlag = [Screen](Screen)('[Preference](Preference)', 'TextAlphaBlending', [enableFlag]);  
oldSize = [Screen](Screen)('[Preference](Preference)', 'DefaultFontSize', [fontSize]);  
oldStyleFlag = [Screen](Screen)('[Preference](Preference)', 'DefaultFontStyle', [styleFlag]);  
oldfontName = [Screen](Screen)('[Preference](Preference)', 'DefaultFontName', [fontName]);  
oldEnableFlag = [Screen](Screen)('[Preference](Preference)', 'DefaultTextYPositionIsBaseline',  
[enableFlag]);  
oldEnableFlag = [Screen](Screen)('[Preference](Preference)', 'TextAntiAliasing', [enableFlag=-1 (System  
setting), 0 = Disable, 1 = Enable, 2 = [EnableHighQuality](EnableHighQuality)]);  
oldEnableFlag = [Screen](Screen)('[Preference](Preference)', 'TextRenderer', [enableFlag=0 (Legacy  
OS-specific), 1 = [HighQ](HighQ) OS-specific (Default), 2 = Linux renderer plugin]);  
oldLocaleNameString = [Screen](Screen)('[Preference](Preference)', 'TextEncodingLocale',  
[newLocalenNameString]);  
oldEnableFlag = [Screen](Screen)('[Preference](Preference)', 'SkipSyncTests', [enableFlag]);  
[maxStddev, minSamples, maxDeviation, maxDuration] = [Screen](Screen)('[Preference](Preference)',  
'SyncTestSettings' [, maxStddev=0.001 secs][, minSamples=50][,  
maxDeviation=0.1][, maxDuration=5 secs]);  
oldEnableFlag = [Screen](Screen)('[Preference](Preference)', 'FrameRectCorrection', [enableFlag=1]);  
oldLevel = [Screen](Screen)('[Preference](Preference)', 'VisualDebugLevel', level);  
  
Workaround flags to work around all kind of deficient drivers and hardware:  
See 'help ConserveVRAMSettings' for settings and their effect.  
  
oldMode = [Screen](Screen)('[Preference](Preference)', 'ConserveVRAM', mode);  
  
Activate compatibility mode: Try to behave like the old [MacOS](MacOS)-9 Psychtoolbox:  
oldEnableFlag = [Screen](Screen)('[Preference](Preference)', 'EmulateOldPTB', [enableFlag]);  
  
oldEnableFlags = [Screen](Screen)('[Preference](Preference)', 'Enable3DGraphics', [enableFlags]);  
oldEnableFlag = [Screen](Screen)('[Preference](Preference)', 'SuppressAllWarnings', [enableFlag]);  
oldMode = [Screen](Screen)('[Preference](Preference)', 'VBLTimestampingMode', [newmode]);  
[oldVTOTAL, oldmaxVTOTALFactor] = [Screen](Screen)('[Preference](Preference)', 'VBLEndlineOverride' [,  
newVTOTAL=auto][, maxVTOTALFactor=1.25]);  
oldMode = [Screen](Screen)('[Preference](Preference)', 'DefaultVideocaptureEngine', [newmode  
(0=Quicktime - unsupported, 1=[LibDC1394](LibDC1394)-Firewire, 2=[LibARVideo](LibARVideo) - unsupported,  
3=[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)))]);  
oldMode = [Screen](Screen)('[Preference](Preference)', 'OverrideMultimediaEngine', [newmode  
(0=Legacy-Quicktime - unsupported, 1=[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)))]);  
oldLevel = [Screen](Screen)('[Preference](Preference)', 'WindowShieldingLevel', [newLevel (0 = Behind  
all other windows - 2000 = In front of all other windows, the default)]);  
residuals = [Screen](Screen)('[Preference](Preference)', 'SynchronizeDisplays', syncMethod [,  
screenId]);  
oldMappings = [Screen](Screen)('[Preference](Preference)', 'ScreenToHead', screenId [, newHeadId,  
newCrtcId][, rank=0]);  
oldLevel = [Screen](Screen)('[Preference](Preference)', 'Verbosity' [,level]);  


###See also:

