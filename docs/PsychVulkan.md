# [PsychVulkan](PsychVulkan)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[PsychVulkan](PsychVulkan) - Interface with the Vulkan graphics and compute api for special purpose tasks.  
  
This function allows to utilize the Khronos Vulkan rendering and compute api  
for special purpose display tasks on suitable operating systems with suitable  
Vulkan v1.1+ capable graphics and display hardware.  
  
Most often you won't call this function directly, but Psychtoolbox will call  
it appropriately from the [PsychImaging](PsychImaging)() function. Read relevant sections  
related to Vulkan in 'help PsychImaging' first, before venturing into the  
functions offered by this function!  
  
# Commands and their meaning  
  
oldVerbosity = [PsychVulkan](PsychVulkan)('Verbosity' [, verbosity]);  
- Returns and optionally sets level of 'verbosity' for driver debug output.  
  'verbosity' = New level of verbosity: 0 = Silent, 1 = Errors only, 2 = Warnings,  
  3 = Info, 4 = Debug, 5 -- ... = Higher debug levels.  
  
  
isSupported = [PsychVulkan](PsychVulkan)('Supported');  
- Returns if use of the Vulkan rendering and display api is in principle supported  
  on this setup. 1 = Supported, 0 = No driver, hardware or operating system support.  
  
oldFlags = [PsychVulkan](PsychVulkan)('OverrideFlags' [, flags]);  
- Returns and optionally sets override for 'flags' parameter in low-level  
  function [PsychVulkan](PsychVulkan)('PerformPostWindowOpenSetup' ..., flags ...); for  
  driver debugging and testing. By default, override flags are not set or  
  used.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/PsychVulkan.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/PsychVulkan.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/PsychVulkan.m</code>
</div>

