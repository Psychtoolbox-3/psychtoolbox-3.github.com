# [PsychVulkanCore('Present')](PsychVulkanCore-Present) 
##### [Psychtoolbox](Psychtoolbox)>[PsychVulkanCore](PsychVulkanCore).{mex*} subfunction

[tPredictedOnset, frameIndex] = PsychVulkanCore('Present', vulkanWindowHandle [, tWhen=0][, doTimestamp=2]);

Present last rendered frame to Vulkan window 'vulkanWindowHandle'.  
  
This will commit the current set of 2D textures with new rendered content to the  
swapchains, for consumption by the presentation engine. You usually won't call  
this function yourself, but [Screen](Screen)('[Flip](Flip)') will call it automatically for you at  
the appropriate moment.  
  
'doTimestamp' If set to 1 or 2, performs timestamping of stimulus onset, or at  
least tries to estimate such onset time. If set to 0, do nothing  
timestamping-wise. A value of 1 always uses a home-made method of scheduling and  
timestamping. A value of 2 tries to use a Vulkan-provided high-precision method  
if available and possible, and falls back to method 1 otherwise. Value 2 is the  
default.  
  
'tWhen' If provided, defines the target presentation time, as provided by  
[Screen](Screen)('[Flip](Flip)', win, tWhen); a value of zero, or omission, means to present as  
soon as possible.  
  
'tPredictedOnset' returns predicted onset time for the just presented frame.  
  
'frameIndex' Running index of just presented (or queued for presentation) frame.  
  
  
  


###See also:

