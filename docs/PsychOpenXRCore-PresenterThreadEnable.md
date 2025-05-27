# [PsychOpenXRCore('PresenterThreadEnable')](PsychOpenXRCore-PresenterThreadEnable) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

oldEnable = PsychOpenXRCore('PresenterThreadEnable', openxrPtr [, enableThread]);

Enable or disable asynchronous background presenter thread for [OpenXR](OpenXR) device  
'openxrPtr'.  
The thread is required on some [OpenXR](OpenXR) runtimes in some situations to provide  
stable visual stimulation if a user script doesn't run an active tracking -\>  
render -\> present loop, or runs the loop too slow / with pauses. It may also be  
needed for timed stimulus presentation, or for half-way reasonable visual  
stimulus onset timestamping. This is all highly dependent on the [OpenXR](OpenXR) runtime  
in use. If possible, the thread should be avoided for better performance.  
This returns the current setting in 'oldEnable'. Optionally you can specify a  
new setting as 'enableThread'. enableThread must be either:  
0 = Disable thread, all operations are done synchronously, driven by the user  
script.  
1 = Enable thread for driving the visual updating loop, independent of user  
script.  
  
  


###See also:
Start Stop [GetTrackingState](PsychOpenXRCore-GetTrackingState) [NeedLocateForProjectionLayers](PsychOpenXRCore-NeedLocateForProjectionLayers)
