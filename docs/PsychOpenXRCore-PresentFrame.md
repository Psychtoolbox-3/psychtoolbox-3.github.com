# [PsychOpenXRCore('PresentFrame')](PsychOpenXRCore-PresentFrame) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

[tPredictedOnset, tPredictedFutureOnset] = PsychOpenXRCore('PresentFrame', openxrPtr [, when=0]);

Present last rendered frame to [OpenXR](OpenXR) display device 'openxrPtr'.  
  
This will commit the current set of 2D textures with new rendered content to the  
texture swapchains, for consumption by the XR runtime/compositor, and a present  
is requested to the compositor. The swapchains will advance, providing new  
unused image textures as new render targets for the next cycle.  
  
You usually won't call this function yourself, but [Screen](Screen)('[Flip](Flip)') will call it  
automatically for you at the appropriate moment.  
  
'when' If provided, defines the target presentation time, as provided by  
[Screen](Screen)('[Flip](Flip)', win, when); A value of zero, or omission, means to present as  
soon as possible. The earliest possibility for such an immediate present would  
be the 'tPredictedFutureOnset' time from the preceeding 'PresentFrame' call.  
  
Return values:  
'tPredictedOnset' Predicted onset time for the just submitted frame, according  
to compositor, as [Screen](Screen)('[Flip](Flip)') return value. A value of 0 means the frame  
present was skipped. A value of -1 means presentation failure.  
'tPredictedFutureOnset' Predicted best-case onset time for the next/future  
submitted frame, according to compositor.  
  
  


###See also:

