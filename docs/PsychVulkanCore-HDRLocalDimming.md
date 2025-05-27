# [PsychVulkanCore('HDRLocalDimming')](PsychVulkanCore-HDRLocalDimming) 
##### [Psychtoolbox](Psychtoolbox)>[PsychVulkanCore](PsychVulkanCore).{mex*} subfunction

oldlocalDimmmingEnable = PsychVulkanCore('HDRLocalDimming', vulkanWindow [, localDimmmingEnable]);

Return and/or set HDR local backlight dimming enable setting for Vulkan  
presentation window 'vulkanWindow'.  
This function returns the currently set HDR local backlight dimming setting for  
dynamic contrast control on the HDR display monitor associated with Vulkan  
window 'vulkanWindow'.  
Return argument 'oldlocalDimmmingEnable' is the current setting.  
The optional 'localDimmingEnable' is the new setting to apply. This will only  
work if the display and display driver supports the VK\_AMD\_display\_native\_hdr  
Vulkan extension. As of June 2020, only "AMD [FreeSync2](FreeSync2) HDR compliant" HDR  
monitors under Windows-10 with an AMD graphics card in fullscreen mode support  
this.  
The [PsychVulkanCore](PsychVulkanCore)('GetHDRProperties', vulkanWindow) function allows to query  
if the current setup supports this function. Please note that this function will  
always report the selected 'localDimmingEnable' setting made by your code on a  
nominally supported setup. There is no way for our driver to detect if the mode  
change on the display was accepted, as the operating system provides no feedback  
about this. At least one model of "compatible" monitor is already known to  
ignore this setting, unknown if this is an AMD driver bug or monitor firmware  
bug. Tread carefully! Manual control of this setting on the monitor itself may  
be the safer choice.  
  


###See also:
[GetHDRProperties](PsychVulkanCore-GetHDRProperties)
