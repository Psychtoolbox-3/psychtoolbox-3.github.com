# [MultiWindowVulkanTest](MultiWindowVulkanTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[MultiWindowVulkanTest](MultiWindowVulkanTest)([nmax=inf][, reverse=0][, screenId=max])  
  
Test multi-window / multi-display operation in fullscreen exclusive direct  
display mode under Linux/X11 with Vulkan.  
  
This mostly for regression testing. Currently, as of October 2021, requires  
an AMD gpu with amdvlk installed. Or launching multiple instances in separate  
processes if you want to test with non-amdvlk drivers (radv) or other gpu's  
like Intel, Adreno etc.  
The script allowed to diagnose and fix a X-Server bug in [RandR](RandR) output leasing,  
bug fix is part of master, should be part of X-Server 21.1, maybe with a bit  
of luck at some point also of server 1.20. For reference, server master commit:  
  
https://gitlab.freedesktop.org/xorg/xserver/-/commit/f467f85ca1f780d5c7cf3c20888e399708d761ac  
  
Press any key to close all fullscreen windows again, after they've been opened,  
and end the test.  
  
### Optional parameters:  
  
'nmax' number of outputs to test simultaneously.  
'reverse' Test closing windows in reverse order if set to 1.  
'screenId' Which screen to test.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/MultiWindowVulkanTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/MultiWindowVulkanTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/MultiWindowVulkanTest.m</code>
</div>

