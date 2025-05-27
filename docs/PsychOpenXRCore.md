# [PsychOpenXRCore](PsychOpenXRCore)
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore)

PsychOpenXRCore - A Psychtoolbox driver for OpenXR compatible VR/AR/MR/XR hardware.  
This driver allows to use XR devices supported by a suitable OpenXR runtime of version 1.x.  
  
Copyright (c) 2022-2025 Mario Kleiner.  
The PsychOpenXRCore driver is licensed to you under the terms of the MIT license.  
  
For some experimental Monado specific timestamping implementation, the driver currently  
also contains a statically included copy of the nanopb protobuffer parsing library  
(URL: https://jpa.kapsi.fi/nanopb) which is licensed under the zlib license, and statically   
included copies of some files from the FOSS Monado OpenXR runtime (https://monado.freedesktop.org),   
which are licensed under the Boost Software License BSL-1.0 - SPDX-License-Identifier: BSL-1.0.  
The statically included files can be found in the nanopb subfolder of the PsychOpenXRCore source folder.  
  
See 'help License.txt' in the Psychtoolbox root folder for more details.  
  
Usage:  
  
Functions used by regular user scripts (but mostly indirectly via PsychVRHMD() or PsychOpenXR()):  
  
oldVerbosity = PsychOpenXRCore('[Verbosity](PsychOpenXRCore-Verbosity)' [, verbosity]);  
numDevices = PsychOpenXRCore('[GetCount](PsychOpenXRCore-GetCount)');  
[openxrPtr, modelName, runtimeName, hasEyeTracking, hasHandTracking] = PsychOpenXRCore('[Open](PsychOpenXRCore-Open)' [, deviceIndex=0]);  
PsychOpenXRCore('[Close](PsychOpenXRCore-Close)' [, openxrPtr]);  
controllerTypes = PsychOpenXRCore('[Controllers](PsychOpenXRCore-Controllers)', openxrPtr);  
[oldType, spaceSize] = PsychOpenXRCore('[ReferenceSpaceType](PsychOpenXRCore-ReferenceSpaceType)', openxrPtr [, newType]);  
oldType = PsychOpenXRCore('[ViewType](PsychOpenXRCore-ViewType)', openxrPtr [, viewLayerType]);  
[oldPosition, oldSize, oldOrientation] = PsychOpenXRCore('[View2DParameters](PsychOpenXRCore-View2DParameters)', openxrPtr, eye [, position][, size][, orientation]);  
oldNeed = PsychOpenXRCore('[NeedLocateForProjectionLayers](PsychOpenXRCore-NeedLocateForProjectionLayers)', openxrPtr [, needLocate]);  
oldEnable = PsychOpenXRCore('[PresenterThreadEnable](PsychOpenXRCore-PresenterThreadEnable)', openxrPtr [, enableThread]);  
PsychOpenXRCore('[Start](PsychOpenXRCore-Start)', openxrPtr);  
PsychOpenXRCore('[Stop](PsychOpenXRCore-Stop)', openxrPtr);  
[state, touch, gaze, hands] = PsychOpenXRCore('[GetTrackingState](PsychOpenXRCore-GetTrackingState)', openxrPtr [, predictionTime=nextFrame][, reqMask=all]);  
input = PsychOpenXRCore('[GetInputState](PsychOpenXRCore-GetInputState)', openxrPtr, controllerType);  
pulseEndTime = PsychOpenXRCore('[HapticPulse](PsychOpenXRCore-HapticPulse)', openxrPtr, controllerType [, duration=2.5][, freq][, amplitude=1.0]);  
[projL, projR, fovL, fovR] = PsychOpenXRCore('[GetStaticRenderParameters](PsychOpenXRCore-GetStaticRenderParameters)', openxrPtr [, clipNear=0.01][, clipFar=10000.0]);  
  
Functions usually only used internally by Psychtoolbox:  
  
[width, height, recMSAASamples, maxMSAASamples, maxWidth, maxHeight] = PsychOpenXRCore('[GetFovTextureSize](PsychOpenXRCore-GetFovTextureSize)', openxrPtr, eye);  
videoRefreshDuration = PsychOpenXRCore('[CreateAndStartSession](PsychOpenXRCore-CreateAndStartSession)', openxrPtr, deviceContext, openGLContext, openGLDrawable, openGLConfig, openGLVisualId, use3DMode, multiThreaded [, srcTexIds]);  
[width, height, numTextures, imageFormat] = PsychOpenXRCore('[CreateRenderTextureChain](PsychOpenXRCore-CreateRenderTextureChain)', openxrPtr, eye, width, height, floatFormat, numMSAASamples);  
texObjectHandle = PsychOpenXRCore('[GetNextTextureHandle](PsychOpenXRCore-GetNextTextureHandle)', openxrPtr, eye);  
[tPredictedOnset, tPredictedFutureOnset] = PsychOpenXRCore('[PresentFrame](PsychOpenXRCore-PresentFrame)', openxrPtr [, when=0]);  
timingSupport = PsychOpenXRCore('[TimingSupport](PsychOpenXRCore-TimingSupport)' [, openxrPtr]);  
  



