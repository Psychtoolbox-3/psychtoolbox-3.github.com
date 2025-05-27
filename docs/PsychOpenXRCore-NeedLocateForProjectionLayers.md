# [PsychOpenXRCore('NeedLocateForProjectionLayers')](PsychOpenXRCore-NeedLocateForProjectionLayers) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

oldNeed = PsychOpenXRCore('NeedLocateForProjectionLayers', openxrPtr [, needLocate]);

Specify if projection layers need to be continuously updated by tracking for  
[OpenXR](OpenXR) device 'openxrPtr'.  
This returns the current setting in 'oldNeed'. Optionally you can specify a new  
setting as 'needLocate'. needLocate must be either:  
0 = Positioning of projection layers stays stable and fixed without a constantly  
running tracking loop on high quality runtimes.  
1 = Projection layers need a constantly running loop, or jitter, jerks, wrong  
positioning or timeout warnings will happen. Note that if this setting is  
needed, then also multi-threaded presentation must be active whenever the user  
script does not engage in fast active tracking via  
[PsychOpenXRCore](PsychOpenXRCore)('GetTrackingState') calls, usually called implicitely via  
[PsychVRHMD](PsychVRHMD)('PrepareRender').  
  
  


###See also:
Start Stop [GetTrackingState](PsychOpenXRCore-GetTrackingState) [PresenterThreadEnable](PsychOpenXRCore-PresenterThreadEnable)
