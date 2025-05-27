# [PsychOpenHMDVRCore](PsychOpenHMDVRCore)
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenHMDVRCore](PsychOpenHMDVRCore)

PsychOpenHMDVRCore - A Psychtoolbox driver for VR hardware supported by OpenHMD.  
  
This driver allows to control OpenHMD supported hardware like Rift DK1/DK2/CV1, HTC Vive, PSVR.  
  
The PsychOpenHMDVRCore driver is licensed to you under the terms of the MIT license.  
See 'help License.txt' in the Psychtoolbox root folder for more details.  
  
The driver requires the OpenHMD library version 0.3+ to work, which is  
distributed under the Boost 1.0 license: http://www.openhmd.net  
  
Usage:  
  
  
oldVerbosity = PsychOpenHMDVRCore('[Verbosity](PsychOpenHMDVRCore-Verbosity)' [, verbosity]);  
numHMDs = PsychOpenHMDVRCore('[GetCount](PsychOpenHMDVRCore-GetCount)');  
[openhmdPtr, modelName, panelSizeX, panelSizeY, controllerTypes, controllerFlags] = PsychOpenHMDVRCore('[Open](PsychOpenHMDVRCore-Open)' [, deviceIndex=0]);  
PsychOpenHMDVRCore('[Close](PsychOpenHMDVRCore-Close)' [, openhmdPtr]);  
oldPersistence = PsychOpenHMDVRCore('[SetLowPersistence](PsychOpenHMDVRCore-SetLowPersistence)', openhmdPtr [, lowPersistence]);  
PsychOpenHMDVRCore('[Start](PsychOpenHMDVRCore-Start)', openhmdPtr);  
PsychOpenHMDVRCore('[Stop](PsychOpenHMDVRCore-Stop)', openhmdPtr);  
input = PsychOpenHMDVRCore('[GetInputState](PsychOpenHMDVRCore-GetInputState)', openhmdPtr, controllerType);  
[state, touch] = PsychOpenHMDVRCore('[GetTrackingState](PsychOpenHMDVRCore-GetTrackingState)', openhmdPtr [, predictionTime=0]);  
pulseEndTime = PsychOpenHMDVRCore('[HapticPulse](PsychOpenHMDVRCore-HapticPulse)', openhmdPtr, controllerType [, duration=2.5][, freq=1.0][, amplitude=1.0]);  
[projL, projR, ipd] = PsychOpenHMDVRCore('[GetStaticRenderParameters](PsychOpenHMDVRCore-GetStaticRenderParameters)', openhmdPtr [, clipNear=0.01][, clipFar=10000.0]);  
[eyePose, eyeIndex, glModelviewMatrix] = PsychOpenHMDVRCore('[GetEyePose](PsychOpenHMDVRCore-GetEyePose)', openhmdPtr, renderPass);  
[width, height, fovPort] = PsychOpenHMDVRCore('[GetFovTextureSize](PsychOpenHMDVRCore-GetFovTextureSize)', openhmdPtr, eye, metersPerTanAngleAtCenter [, fov=[HMDRecommended]]);  
[width, height, hmdShiftx, hmdShifty, hmdShiftz, abberation, distortion, scrnHorSize, scrnVertSize] = PsychOpenHMDVRCore('[GetUndistortionParameters](PsychOpenHMDVRCore-GetUndistortionParameters)', openhmdPtr, eye [, inputWidth][, inputHeight][, fov]);  
[vertexShaderSrc, fragmentShaderSrc] = PsychOpenHMDVRCore('[GetCorrectionShaders](PsychOpenHMDVRCore-GetCorrectionShaders)', openhmdPtr);  
  



