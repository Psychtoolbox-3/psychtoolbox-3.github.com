# [PsychVulkanCore('GetHDRProperties')](PsychVulkanCore-GetHDRProperties) 
##### [Psychtoolbox](Psychtoolbox)>[PsychVulkanCore](PsychVulkanCore).{mex*} subfunction

hdr = PsychVulkanCore('GetHDRProperties', vulkanWindow);

Return HDR properties of Vulkan presentation window 'vulkanWindow'.  
'hdr' is a struct with information about the HDR properties and settings for the  
display and window represented by 'vulkanWindow'. The following fields are  
defined:  
'GPUIndex' = Index of the Vulkan device used for this window.  
'Valid' = Are the HDR display properties valid? 0 = No, as no data could be  
queried from the display, 1 = Yes, data has been queried from display and is  
supposed to represent actual display HDR capabilities and properties.  
'HDRMode' 0 = None (SDR), 1 = Basic HDR-10 enabled with BT-2020 color space, 10  
bpc color precision, and ST-2084 PQ Perceptual Quantizer EOTF.  
'LocalDimmingControl' 0 = No, 1 = Local dimming control supported.  
'MinLuminance' Minimum supported luminance in nits.  
'MaxLuminance' Maximum supported peak / burst luminance in nits.  
'MaxFrameAverageLightLevel' Maximum sustainable supported luminance in nits.  
'MaxContentLightLevel' Maximum desired content light level in nits.  
'ColorGamut' A 2-by-4 matrix encoding the CIE-1931 2D chromaticity coordinates  
of the red, green, and blue color primaries in columns 1, 2 and 3, and the  
white-point in column 4.  
'ColorSpace' Vulkan colorspace used for display. See [VkColorSpaceKHR](VkColorSpaceKHR) spec for  
reference.  
'ColorFormat' Vulkan pixel color format used for display. See [VkFormat](VkFormat) spec for  
reference.  
'ColorPrecision' Effective color precision of the Vulkan interop image and  
Vulkan swapChain: 0 = GL\_RGBA8, 1 = GL\_RGB10A2, 2 = GL\_RGBA16F, 3 = GL\_RGBA16.  
  
  


###See also:
[OpenWindow](PsychVulkanCore-OpenWindow) [HDRMetadata](PsychVulkanCore-HDRMetadata)
