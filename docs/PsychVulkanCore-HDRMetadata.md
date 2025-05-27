# [PsychVulkanCore('HDRMetadata')](PsychVulkanCore-HDRMetadata) 
##### [Psychtoolbox](Psychtoolbox)>[PsychVulkanCore](PsychVulkanCore).{mex*} subfunction

oldHdrMetadata = PsychVulkanCore('HDRMetadata', vulkanWindow, metadataType [, maxFrameAverageLightLevel][, maxContentLightLevel][, minLuminance][, maxLuminance][, colorGamut]);

Return and/or set HDR metadata for Vulkan presentation window 'vulkanWindow'.  
This function returns the currently defined HDR metadata that is sent to the HDR  
display monitor associated with Vulkan window 'vulkanWindow', according to the  
format specified by the mandatory 'metadataType' parameter. It optionally allows  
to define new HDR metadata to send to the monitor, starting with the next  
presented visual stimulus image, ie. at the completion of the next  
[Screen](Screen)('[Flip](Flip)') or [PsychVulkanCore](PsychVulkanCore)('Present').  
Note: Setting new HDR metadata can be an expensive - and potentially visually  
disruptive - operation with some graphics drivers on some operating system,  
e.g., on MS-Windows. Therefore avoid too frequent updates. Our driver will  
eliminate redundant updates as a simple performance optimization.  
Return argument 'oldHdrMetadata' is a struct with information about the current  
metadata. Optionally you can define new metadata to be sent to the display. If  
you specify any new settings, but omit any values or leave them [] empty, then  
those values will remain at their current / old values.  
The following fields in the struct and as new settings are defined:  
'MetadataType' Mandatory: Type of metadata to send or query. Currently only a  
value of 0 is supported, which defines "Static HDR metadata type 1", as  
specified by the standards SMPTE 2086 for the mastering display color properties  
(~ color volume) and CTA-861.3 / CTA-861-G standards for content light levels.  
This type of metadata allows for luminance levels between 0 and 65535 nits,  
except for 'MinLuminance' which allows for a maximum of 6.5535 nits.  
The content light level properties 'MaxFrameAverageLightLevel' and  
'MaxContentLightLevel' default to 0 at startup, which signals to the display  
device that they are unknown, a reasonable assumption for dynamically rendered  
content with prior unknown maximum values over a whole session.  
'MaxFrameAverageLightLevel' Maximum frame average light level of the visual  
content in nits [0; 65535].  
'MaxContentLightLevel' Maximum light level of the visual content in nits [0;  
65535].  
The following mastering display properties (~ color volume) default to the  
properties of the used HDR display monitor for presentation, if they could be  
queried from the connected monitor. It is advisable to override them with the  
real properties of the mastering display, e.g., for properly mastered movie  
content or image files where this information may be available.  
'MinLuminance' Minimum supported luminance of the mastering display in nits [0;  
6.5535].  
'MaxLuminance' Maximum supported luminance of the mastering display in nits [0;  
65535].  
'ColorGamut' A 2-by-4 matrix encoding the CIE-1931 2D chromaticity coordinates  
of the red, green, and blue color primaries in columns 1, 2, and 3, and the  
location of the white-point in column 4. This defines the color space and gamut  
in which the visual content was produced.  
  
  


###See also:
[OpenWindow](PsychVulkanCore-OpenWindow) [GetHDRProperties](PsychVulkanCore-GetHDRProperties) Present
