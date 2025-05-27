# [PsychVulkanCore](PsychVulkanCore)
##### [Psychtoolbox](Psychtoolbox)>[PsychVulkanCore](PsychVulkanCore)

PsychVulkanCore - A Psychtoolbox driver for interfacing with the Vulkan graphics rendering API  
  
This driver allows to utilize the Vulkan graphics API for special purpose display and compute tasks.  
Copyright (c) 2020 - 2024 Mario Kleiner. Licensed to you under the terms of the MIT license.  
  
This driver is used internally by Psychtoolbox. You should not call its functions  
directly as a regular end-user from your scripts, as the API may change at any time  
in a backwards incompatible way without any warning! The driver may even go away  
completely in a future version of Psychtoolbox if its functionality gets more tightly  
integrated into other mex files!  
  
Functions used internally by Psychtoolbox:  
  
oldVerbosity = PsychVulkanCore('[Verbosity](PsychVulkanCore-Verbosity)' [, verbosity]);  
numDevices = PsychVulkanCore('[GetCount](PsychVulkanCore-GetCount)');  
devices = PsychVulkanCore('[GetDevices](PsychVulkanCore-GetDevices)');  
PsychVulkanCore('[Close](PsychVulkanCore-Close)');  
vulkanWindow = PsychVulkanCore('[OpenWindow](PsychVulkanCore-OpenWindow)', gpuIndex, targetUUID, isFullscreen, screenId, rect, outputHandle, hdrMode, colorPrecision, refreshHz, colorSpace, colorFormat, flags);  
PsychVulkanCore('[CloseWindow](PsychVulkanCore-CloseWindow)' [, vulkanWindow]);  
hdr = PsychVulkanCore('[GetHDRProperties](PsychVulkanCore-GetHDRProperties)', vulkanWindow);  
oldlocalDimmmingEnable = PsychVulkanCore('[HDRLocalDimming](PsychVulkanCore-HDRLocalDimming)', vulkanWindow [, localDimmmingEnable]);  
[interopObjectHandle, allocationSize, formatSpec, tilingMode, memoryOffset, width, height, interopSemaphoreHandle] = PsychVulkanCore('[GetInteropHandle](PsychVulkanCore-GetInteropHandle)', vulkanWindowHandle [, wantSemaphore=0][, eye=0]);  
oldHdrMetadata = PsychVulkanCore('[HDRMetadata](PsychVulkanCore-HDRMetadata)', vulkanWindow, metadataType [, maxFrameAverageLightLevel][, maxContentLightLevel][, minLuminance][, maxLuminance][, colorGamut]);  
[tPredictedOnset, frameIndex] = PsychVulkanCore('[Present](PsychVulkanCore-Present)', vulkanWindowHandle [, tWhen=0][, doTimestamp=2]);  
  



