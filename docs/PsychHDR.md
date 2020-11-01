# [PsychHDR](PsychHDR)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[PsychHDR](PsychHDR) - Support and control stimulus display to HDR "High dynamic range" displays.  
  
This driver provides both, the setup code for the HDR main setup command  
[PsychImaging](PsychImaging)('AddTask', 'General', 'EnableHDR'), to get HDR display enabled  
for a specific Psychtoolbox onscreen window on a specific HDR display, and  
utility subfunctions for user-scripts to call after initial setup, to modify  
HDR display behaviour.  
  
HDR currently only works on graphics card + operating system combinations which  
support both the [OpenGL](OpenGL) and Vulkan rendering api's and also efficient [OpenGL](OpenGL)-Vulkan  
interoperation. Additionally, the Vulkan driver, graphics card, and your display  
device must support at least the HDR-10 standard for high dynamic range display.  
  
### As of October 2020, these graphics cards would be suitable:  
  
- Modern AMD (RX 500 "Polaris" and later recommended) and [NVidia](NVidia) [(GeForce]((GeForce) 1000  
  "Pascal" and later recommended) graphics cards under a Windows-10 system, which  
  is up to date for the year 2020.  
  
- Modern AMD graphics cards (like above) under modern GNU/Linux (Ubuntu 18.04.4-LTS  
  at a minimum (untested!), or better Ubuntu 20.04-LTS and later recommended), with  
  the AMD open-source Vulkan driver "amdvlk". Install driver release 2020-Q3.5 from  
  September 2020, or later versions. This webpage has amdvlk download and installation  
  instructions:  
  
  https://github.com/[GPUOpen](GPUOpen)-Drivers/AMDVLK/releases  
  
### HDR functionality is demonstrated in multiple demos:  
  
[SimpleHDRDemo](SimpleHDRDemo).m as a simple starter for basic image display and rendering.  
[HDRViewer](HDRViewer).m as a more fancy static image viewer.  
[HDRTest](HDRTest).m for testing HDR reproduction with a colorimeter supported by Psychtoolbox.  
[MinimalisticOpenGLDemo](MinimalisticOpenGLDemo).m with the optional 'hdr' parameter set to 1 for most basic [OpenGL](OpenGL) rendering in HDR.  
[PlayMoviesDemo](PlayMoviesDemo).m with the optional 'hdr' parameter set to 1 for playback of HDR movies.  
  
Useful helper functions beyond [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableHDR');  
for basic HDR setup and configuration, and [PsychHDR](PsychHDR)() for tweaking, are  
the [HDRRead](HDRRead)() command for reading some HDR image file formats, e.g.,  
Radiance .hdr or [OpenEXR](OpenEXR) .exr, [ComputeHDRStaticMetadataType1ContentLightLevels](ComputeHDRStaticMetadataType1ContentLightLevels)()  
for computing HDR static metadata type one for an image or stack of  
images, and [ConvertRGBSourceToRGBTargetColorSpace](ConvertRGBSourceToRGBTargetColorSpace)() for converting images  
from a source color space / gamut to a destination color space / gamut.  
  
  
Most often you won't call this function directly, but Psychtoolbox will call  
it appropriately from the [PsychImaging](PsychImaging)() function. Read relevant sections  
related to 'EnableHDR' in 'help PsychImaging' first, before venturing into the  
subfunctions offered by this function.  
  
# User accessible commands and their meaning  
  
oldVerbosity = [PsychHDR](PsychHDR)('Verbosity' [, verbosity]);  
- Returns and optionally sets level of 'verbosity' for driver debug output.  
  'verbosity' = New level of verbosity: 0 = Silent, 1 = Errors only, 2 = Warnings,  
  3 = Info, 4 = Debug, 5 -- ... = Higher debug levels.  
  
  
isSupported = [PsychHDR](PsychHDR)('Supported');  
- Returns if HDR visual stimulus display is in principle supported on this setup.  
  1 = Supported, 0 = No driver, hardware or operating system support.  
  
  
hdrProperties = [PsychHDR](PsychHDR)('GetHDRProperties', window);  
- Returns hdrProperties, a struct with information about the HDR display properties  
  of the onscreen window 'window'. Most importantly, it returns information about the  
  native color gamut of the HDR display device and its brightness range. The following  
  fields in hdrProperties exist at least:  
  
  'Valid'   Are the HDR display properties valid? 0 = No, as no data could be  
            queried from the display, 1 = Yes, data has been queried from display and is  
            supposed to represent actual display HDR capabilities and properties.  
  
  'HDRMode' 0 = None (SDR), 1 = Basic HDR-10 enabled with BT-2020 color space, 10  
            bpc color precision, and ST-2084 PQ Perceptual Quantizer EOTF.  
  
  'LocalDimmingControl' 0 = No, 1 = Local dimming control supported.  
  
  'MinLuminance' Minimum supported luminance in nits.  
  
  'MaxLuminance' Maximum supported peak / burst luminance in nits. This is often  
                 only achievable for a small area of the display surface over extended  
                 periods of time, e.g., only for 10% of the pixel area. The full display  
                 may only be able to sustain that luminance for a few seconds.  
  
  'MaxFrameAverageLightLevel' Maximum sustainable supported luminance in nits.  
  
  'MaxContentLightLevel' Maximum desired content light level in nits.  
  
  'ColorGamut' A 2-by-4 matrix encoding the CIE-1931 2D chromaticity coordinates of the  
               red, green, and blue color primaries in columns 1, 2 and 3, and  
               the white-point in column 4.  
  
  
oldlocalDimmmingEnable = [PsychHDR](PsychHDR)('HDRLocalDimming', window [, localDimmmingEnable]);  
- Return and/or set HDR local backlight dimming enable setting for display  
  associated with window 'window'.  
  
  This function returns the currently set HDR local backlight dimming setting for  
  dynamic contrast control on the HDR display monitor associated with window  
  'window'.  
  
  Return argument 'oldlocalDimmmingEnable' is the current setting.  
  The optional 'localDimmingEnable' is the new setting to apply. This will only  
  work if the display and display driver supports the VK\_AMD\_display\_native\_hdr  
  Vulkan extension. As of July 2020, only "AMD [FreeSync2](FreeSync2) HDR compliant" HDR  
  monitors under Windows-10 with an AMD graphics card in fullscreen mode support  
  this.  
  
  The hdrProperties = [PsychHDR](PsychHDR)('GetHDRProperties', window); function allows to query  
  if the current setup supports this function. Please note that this function will  
  always report the selected 'localDimmingEnable' setting made by your code on a  
  nominally supported setup. There is no way for our driver to detect if the mode  
  change on the display was accepted, as the operating system provides no feedback  
  about this. At least one model of "compatible" monitor is already known to  
  ignore this setting, unknown if this is an AMD driver bug or monitor firmware  
  bug. Tread carefully! Manual control of this setting on the monitor itself may  
  be the safer choice.  
  
  
a) oldHdrMetadata = [PsychHDR](PsychHDR)('HDRMetadata', window, metadataType [, maxFrameAverageLightLevel][, maxContentLightLevel][, minLuminance][, maxLuminance][, colorGamut]);  
b) oldHdrMetadata = [PsychHDR](PsychHDR)('HDRMetadata', window [, newHdrMetadata]);  
- Return and/or set HDR metadata for presentation window 'window'.  
  
  This function returns the currently defined HDR metadata that is sent  
  to the HDR display associated with the window 'window'. It optionally  
  allows to define new HDR metadata to send to the display, starting with  
  the next presented visual stimulus image, ie. the successfull completion  
  of the next [Screen](Screen)('[Flip](Flip)').  
  
  The mandatory parameter 'metadataType' specifies the format in which  
  HDR metadata should be returned or set.  
  
  Return argument 'oldHdrMetadata' is a struct with information about the  
  current metadata. Optionally you can define new metadata to be sent to  
  the display in one of the two formats a) or b) shown above: Either a)  
  as separate parameters, or b) as a 'newHdrMetadata' struct. If you use  
  the separate parameters format a) and specify any new settings, but  
  omit some of the optional parameter values or leave them [] empty, then  
  those values will remain at their current / old values. If you use the  
  struct format b), then you must pass in a non-empty 'newHdrMetadata'  
  struct which contains the same fields as the struct returned in  
  'oldHdrMetadata', with all fields for the given 'MetadataType' properly  
  defined, otherwise an error will occur. Format b) is useful as a  
  convenience for querying 'oldHdrMetadata', then modifying some of its  
  values, and then passing this modified variant back in as  
  'newHdrMetadata'. For HDR movie playback, [Screen](Screen)('OpenMovie') also  
  optionally returns a suitable hdrStaticMetaData struct in the right  
  format for passing it as 'newHdrMetadata'.  
  
###   The following fields in the struct and as new settings are defined:  
  
  'MetadataType' Type of metadata to send or query. Currently only a  
  value of 0 is supported, which defines "Static HDR metadata type 1", as  
  used and specified by the HDR standards CTA-861-3 / CTA-861-G (content  
  light levels) and SMPTE 2086 (mastering display color properties, ie.  
  color volume).  
  
  The content light level properties 'MaxFrameAverageLightLevel' and  
  'MaxContentLightLevel' default to 0 at startup, which signals to the  
  display device that they are unknown, a reasonable assumption for  
  dynamically rendered content with prior unknown maximum values over a  
  whole session.  
  
  'MaxFrameAverageLightLevel' Maximum frame average light level of the visual  
  content in nits, range 0 - 65535 nits.  
  
  'MaxContentLightLevel' Maximum light level of the visual content in  
  nits, range 0 - 65535 nits.  
  
  The following mastering display properties (~ color volume) default to  
  the properties of the connected HDR display monitor for presentation, if  
  they could be queried from the connected monitor. It is advisable to  
  override them with the real properties of the mastering display, e.g.,  
  for properly mastered movie content or image files where this data may  
  be available.  
  
  'MinLuminance' Minimum supported luminance of the mastering display in  
  nits, range 0 - 6.5535 nits.  
  
  'MaxLuminance' Maximum supported luminance of the mastering display in  
  nits, range 0 - 65535 nits.  
  
  'ColorGamut' A 2-by-4 matrix encoding the CIE-1931 2D chromaticity  
  coordinates of the red, green, and blue color primaries in columns 1,  
  2, and 3, and the location of the white-point in column 4. This defines  
  the color space and gamut in which the visual content was produced.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/PsychHDR.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/PsychHDR.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/PsychHDR.m</code>
</div>

