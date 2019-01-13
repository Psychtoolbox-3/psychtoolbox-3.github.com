# [Eyelink](Eyelink)
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink)

  
% This is the main function of the Eyelink toolbox  
Usage:  
  
% For general advice, try:  
help Eyelink  
  
% For a more detailed explanation of any Eyelink function, just add a question mark "?".  
% E.g. for 'Initialize', try either of these equivalent forms:  
Eyelink('Initialize?')  
Eyelink Initialize?  
  
% If you think you've found a bug, please report it  
on the forum, see: http://psychtoolbox.org/  
  
  
% Initialize or shutdown Eyelink connection:  
[status =] Eyelink('[Initialize](Eyelink-Initialize)' [, displayCallbackFunction])  
[status =] Eyelink('[InitializeDummy](Eyelink-InitializeDummy)' [, displayCallbackFunction])  
[status =] Eyelink('[IsConnected](Eyelink-IsConnected)')  
[status =] Eyelink('[SetAddress](Eyelink-SetAddress)', ipaddress);  
Eyelink('[Shutdown](Eyelink-Shutdown)')  
oldlevel = Eyelink('[Verbosity](Eyelink-Verbosity)' [,level]);  
Eyelink('[TestSuite](Eyelink-TestSuite)')  
[status =] Eyelink('[OpenFile](Eyelink-OpenFile)', filename [, dontOpenExisting=0])  
[status =] Eyelink('[CloseFile](Eyelink-CloseFile)')  
[status =] Eyelink('[ReceiveFile](Eyelink-ReceiveFile)',['filename'], ['dest'], ['dest_is_path'])  
  
% Calibration:  
[result =] Eyelink('[StartSetup](Eyelink-StartSetup)' [, stype=0])  
[status = ] Eyelink('[DriftCorrStart](Eyelink-DriftCorrStart)', x, y [,dtype=0][, dodraw=1][, allow_setup=0])  
[result = ] Eyelink('[ApplyDriftCorr](Eyelink-ApplyDriftCorr)')  
[result, tx, ty] = Eyelink('[TargetCheck](Eyelink-TargetCheck)')  
[result = ] Eyelink('[AcceptTrigger](Eyelink-AcceptTrigger)')  
[result, messageString =] Eyelink('[CalMessage](Eyelink-CalMessage)')  
  
% Start or stop recording and acquiring data:  
[startrecording_error =] Eyelink('[StartRecording](Eyelink-StartRecording)' [,file_samples, file_events, link_samples, link_events] )  
Eyelink('Stoprecording')  
error = Eyelink('[CheckRecording](Eyelink-CheckRecording)')  
eyeused = Eyelink('[EyeAvailable](Eyelink-EyeAvailable)')  
NewOrOld = Eyelink('[NewFloatSampleAvailable](Eyelink-NewFloatSampleAvailable)')  
sample = Eyelink('[NewestFloatSample](Eyelink-NewestFloatSample)')  
[sample, raw] = Eyelink('[NewestFloatSampleRaw](Eyelink-NewestFloatSampleRaw)' [, eye])  
type = Eyelink('[GetNextDataType](Eyelink-GetNextDataType)')  
item = Eyelink('[GetFloatData](Eyelink-GetFloatData)', type)  
[item, raw] = Eyelink('[GetFloatDataRaw](Eyelink-GetFloatDataRaw)', type [, eye])  
[samples, events, drained] = Eyelink('[GetQueuedData](Eyelink-GetQueuedData)'[, eye])  
  
% Miscellaneous functions to communicate with Eyelink:  
result = Eyelink('[ButtonStates](Eyelink-ButtonStates)')  
[status =] Eyelink('[Command](Eyelink-Command)', 'formatstring', [...])  
[status =] Eyelink('[Message](Eyelink-Message)', 'formatstring', [...])  
[result =] Eyelink('[SendKeyButton](Eyelink-SendKeyButton)', code, mods, state)  
[time =] Eyelink('[TrackerTime](Eyelink-TrackerTime)')  
[offset =] Eyelink('[TimeOffset](Eyelink-TimeOffset)')  
[status =] Eyelink('[RequestTime](Eyelink-RequestTime)')  
[time =] Eyelink('[ReadTime](Eyelink-ReadTime)')  
[mode =] Eyelink('[TrackerMode](Eyelink-TrackerMode)')  
[result, reply =] Eyelink('[ReadFromTracker](Eyelink-ReadFromTracker)', VariableName)  
  
% Miscellaneous Eyelink functions:  
[result =] Eyelink('[WaitForModeReady](Eyelink-WaitForModeReady)', maxwait)  
[result =] Eyelink('[ImageModeDisplay](Eyelink-ImageModeDisplay)')  
mode = Eyelink('[CurrentMode](Eyelink-CurrentMode)')  
result = Eyelink('[CalResult](Eyelink-CalResult)')  
Eyelink('[SetOfflineMode](Eyelink-SetOfflineMode)')  
[version, versionString]  = Eyelink('[GetTrackerVersion](Eyelink-GetTrackerVersion)')  
[time =] Eyelink('[TrackerTime](Eyelink-TrackerTime)')  
[offset =] Eyelink('[TimeOffset](Eyelink-TimeOffset)')  
[status] = Eyelink('[ImageTransfer](Eyelink-ImageTransfer)', imagePath [, xPosition=0][, yPosition=0][, width=0][, height=0][, trackerXPosition=0][, trackerYPosition=0][, xferoptions=0])  
  
% Eyelink Velocity related functions:  
[vel, acc, fsample]= Eyelink('CalculateOverallVelocityAndAcceleration' [, sample_model])  
[vel,fsample] = Eyelink('CalculateVelocity' [,sample_model] )  
[x_vel,y_vel,fsample] = Eyelink('CalculateVelocityXY' [,sample_model] )  
  
  
  
  
% EyelinkToolbox version for the OpenGL PsychToolbox  
% The EyelinkToolbox was developed by:  
  
	Frans Cornelissen  
	Enno Peters  
	John Palmer  
	Chris Burns  
	Mario Kleiner  
	Erik Flister  
	Nuha Jabakhanji  
  

  
    The EyelinkToolbox can be used to ceate eye-movement experiments and  
   control the SR-Research Eyelink� gazetrackers  
   (http://www.eyelinkinfo.com/) from within Matlab.  
   It is incorporated into the PsychToolbox (http://www.psychtoolbox.org/).  
   and uses the functions provided by the PsychToolBox for graphics and sound.  
  
   For a complete list of available functions type "Eyelink" in the  
   Matlab command window. For an explanation of any particular Eyelink  
   function just add a question mark "?" after a command.  
    E.g. for 'Initialize', try either of these equivalent forms:  
        Eyelink('Initialize?')  
        Eyelink initialize?  
  
    [optional arguments]:  
    Brackets in the function list, e.g. [remport], indicate optional  
   arguments, not matrices. Optional arguments must be in order, without  
   omitting earlier ones.  
      
    If you need examples to get you started, check out the EyelinkDemos  
   folder.  
          
   More information on this toolbox can be found in the file:  
   EyelinkToolbox/contents.m  
  
  


