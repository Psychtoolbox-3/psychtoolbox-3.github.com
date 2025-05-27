# [PsychOculusVRCore](PsychOculusVRCore)
##### [Psychtoolbox](Psychtoolbox)>[PsychOculusVRCore](PsychOculusVRCore)

PsychOculusVRCore - A Psychtoolbox driver for Oculus VR hardware.  
  
This driver allows to control Oculus Rift DK1/DK2 and hopefully in the future also future Oculus devices.  
  
The PsychOculusVRCore driver is licensed to you under the terms of the MIT license.  
See 'help License.txt' in the Psychtoolbox root folder for more details.  
  
  
  
The driver currently requires the Oculus VR runtime version 0.5.0.1 to work.  
  
  
  
Usage:  
  
  
Functions used by regular user scripts:  
  
  
  
oldVerbosity = PsychOculusVRCore('[Verbosity](PsychOculusVRCore-Verbosity)' [, verbosity]);  
numHMDs = PsychOculusVRCore('[GetCount](PsychOculusVRCore-GetCount)');  
[oculusPtr, modelName] = PsychOculusVRCore('[Open](PsychOculusVRCore-Open)' [, deviceIndex=0]);  
PsychOculusVRCore('[Close](PsychOculusVRCore-Close)' [, oculusPtr]);  
showHSW = PsychOculusVRCore('[GetHSWState](PsychOculusVRCore-GetHSWState)', oculusPtr [, dismiss]);  
oldPersistence = PsychOculusVRCore('[SetLowPersistence](PsychOculusVRCore-SetLowPersistence)', oculusPtr [, lowPersistence]);  
oldDynamicPrediction = PsychOculusVRCore('[SetDynamicPrediction](PsychOculusVRCore-SetDynamicPrediction)', oculusPtr [, dynamicPrediction]);  
PsychOculusVRCore('[Start](PsychOculusVRCore-Start)', oculusPtr);  
PsychOculusVRCore('[Stop](PsychOculusVRCore-Stop)', oculusPtr);  
state = PsychOculusVRCore('[GetTrackingState](PsychOculusVRCore-GetTrackingState)', oculusPtr [, predictionTime=0]);  
[projL, projR] = PsychOculusVRCore('[GetStaticRenderParameters](PsychOculusVRCore-GetStaticRenderParameters)', oculusPtr [, clipNear=0.01][, clipFar=10000.0]);  
[eyePoseL, eyePoseR, tracked, frameTiming] = PsychOculusVRCore('[StartRender](PsychOculusVRCore-StartRender)', oculusPtr);  
[eyePose, eyeIndex] = PsychOculusVRCore('[GetEyePose](PsychOculusVRCore-GetEyePose)', oculusPtr, renderPass);  
  
  
Functions usually only used internally by Psychtoolbox:  
  
  
  
[width, height, fovPort] = PsychOculusVRCore('[GetFovTextureSize](PsychOculusVRCore-GetFovTextureSize)', oculusPtr, eye [, fov=[HMDRecommended]][, pixelsPerDisplay=1]);  
[width, height, viewPx, viewPy, viewPw, viewPh, pptax, pptay, hmdShiftx, hmdShifty, hmdShiftz, meshVertices, meshIndices, uvScaleX, uvScaleY, uvOffsetX, uvOffsetY] = PsychOculusVRCore('[GetUndistortionParameters](PsychOculusVRCore-GetUndistortionParameters)', oculusPtr, eye [, inputWidth][, inputHeight][, fov]);  
[eyeRotStartMatrix, eyeRotEndMatrix] = PsychOculusVRCore('[GetEyeTimewarpMatrices](PsychOculusVRCore-GetEyeTimewarpMatrices)', oculusPtr, eye [, waitForTimewarpPoint=0]);  
PsychOculusVRCore('[EndFrameTiming](PsychOculusVRCore-EndFrameTiming)', oculusPtr);  
result = PsychOculusVRCore('[LatencyTester](PsychOculusVRCore-LatencyTester)', oculusPtr, cmd);  
  



