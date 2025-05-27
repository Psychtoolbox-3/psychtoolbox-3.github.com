# [PsychOpenXRCore('ViewType')](PsychOpenXRCore-ViewType) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

oldType = PsychOpenXRCore('ViewType', openxrPtr [, viewLayerType]);

Specify the type of view for [OpenXR](OpenXR) device 'openxrPtr'.  
This returns the current type of view in 'oldType'. Optionally you can specify a  
new view type as 'viewLayerType'. viewLayerType must be either:  
0 = Use a 2D monoscopic or stereoscopic view via [OpenXR](OpenXR) quad layers, which  
supposedly stays stable for not actively tracked or slow updating stimulus  
display on [OpenXR](OpenXR) conformant runtimes. Placing these views properly for  
binocular / stereoscopic display and perspective correct 3D rendering is your  
scripts responsibility. Cfe. [PsychOpenXRCore](PsychOpenXRCore)('View2DParameters') for setting  
these to non-default values.  
1 = Use a 3D perspective projected view via [OpenXR](OpenXR) projection layers. These are  
auto-configured for good perspective correct 3D rendering, but need an active  
track -\> render -\> present loop on some [OpenXR](OpenXR) runtimes to work correctly,  
otherwise judder and jerks will occur in the display.  
[PsychOpenXRCore](PsychOpenXRCore)('GetTrackingState') drives this manually, usually called via  
[PsychVRHMD](PsychVRHMD)('PrepareRender').  
  
  


###See also:
[View2DParameters](PsychOpenXRCore-View2DParameters) Start Stop [GetTrackingState](PsychOpenXRCore-GetTrackingState) [NeedLocateForProjectionLayers](PsychOpenXRCore-NeedLocateForProjectionLayers)
