# [Datapixx('GetVideoStatus')](Datapixx-GetVideoStatus) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

status = Datapixx('GetVideoStatus');

Returns a struct containing the following video status information:  
-"horizontalResolution" is the number of visible pixels in one horizontal scan  
line  
-"verticalResolution" is the number of visible lines in one vertical frame  
-"horizontalTotal" is the number of video dot times in one horizontal scan line,  
including horizontal blanking interval  
-"verticalTotal" is the number of video lines in one vertical frame, including  
vertical blanking interval  
-"verticalFrequency" is the vertical frame rate in Hz  
-"horizontalFrequency" is the horizontal line rate in Hz  
-"dotFrequency" is the pixel dot rate in Hz  
-"mode" is the video processing mode set by [SetVideoMode](SetVideoMode)  
-"greyscaleMode" is the video greyscale mode set by [SetVideoGreyscaleMode](SetVideoGreyscaleMode)  
-"receivingVideo" is 1 if the Datapixx is currently receiving video data over  
the DVI link. If the video input cable becomes unplugged, or the graphics board  
enters power-saving mode, then receivingVideo will be 0.  
-"receivingDualLinkVideo" is 1 if currently receiving dual-link DVI video, or 0  
for single-link video.  
-"stereoEye" is 1 if the Datapixx is showing left-eye data, or 0 if showing  
right-eye data.  
-"verticalStereo" is 1 if the Datapixx is doubling the refresh rate, showing the  
top and bottom halves of the image on successive video frames, and driving the  
mini-DIN-3 VESA stereo connector for stereo goggles.  
-"stereoBlueline" is 1 if the Datapixx is driving the mini-DIN-3 VESA stereo  
connector, based on blueline codes on the bottom of each video frame.  
-"stereoVesaWaveform" can take on one of the following values:  
 0: VESA port drives straight L/R squarewave for 3rd party emitter.  
 1: VESA port drives 3DPixx IR emitter for [CrystalEyes](CrystalEyes) 3D goggles.  
 2: VESA port drives 3DPixx IR emitter for NVIDIA 3D goggles.  
-"horizontalSplit" is 1 if the Datapixx is showing the left half of the image on  
VGA OUT 1, and the right half of the image on VGA OUT 2. The Datapixx will do  
this automatically if the horizontal resolution is at least twice the vertical  
resolution. If horizontalSplit is 0, then the Datapixx is in mirror mode,  
showing the same image on the two VGA outputs. See [DatapixxDualDisplayInfo](DatapixxDualDisplayInfo).m for  
details.  
-"horizontalOverlay" is 1 if the Datapixx is showing an overlay composite of the  
left/right halves of the video image.  
-"horizontalOverlayBoundsLeft/Right/Top/Bottom" show the extents of the overlay.  
-"pixelSyncTimeout" is 1 if the last call to [RegWrPixelSync](RegWrPixelSync) or [RegWrRdPixelSync](RegWrRdPixelSync)  
timed out.  
-"overClocked" is 1 if the Datapixx is receiving video at too high a clock  
frequency.  
-"pixelSyncRasterLine" is the raster line on which the pixel sync is expected.  
-"pixelSyncSingleLine" is 1 if pixel sync is only recognized on a single line.  
-"pixelSyncBlankLine" is 1 if the pixel sync raster line is displayed black.  
-"scanningBacklight" is 1 if [VIEWPixx](VIEWPixx) scanning backlight is enabled.  
-"backlightIntensity" is the [VIEWPixx](VIEWPixx) LED backlight intensity.  
-"lcd3D60Hz" is 1 if [VIEWPixx](VIEWPixx)/3D pixel polarity inversion is enabled.  
-"videoClutTransparencyColorMode" is 1 if [VIEWPixx](VIEWPixx)/[PROPixx](PROPixx) CLUT overlay had  
enabled transparency.  
-"pixelMode" is 1 if the digital outputs are being driving by the top-left  
pixel's value.  
-"propixxCeilingMount" is 1 if [PROPixx](PROPixx) is flipping image horizontally and  
vertically.  
-"propixxRearProjection" is 1 if [PROPixx](PROPixx) is flipping image horizontally.  
-"propixx3DCrosstalk" is [PROPixx](PROPixx) 3D left <-\> right eye crosstalk elimination  
factor.  
-"propixx3DCrosstalkLR" is [PROPixx](PROPixx) left -\> right eye 3D crosstalk elimination  
factor.  
-"propixx3DCrosstalkRL" is [PROPixx](PROPixx) left <- right eye 3D crosstalk elimination  
factor.  
-"propixxLampLed" is 1 if [PROPixx](PROPixx) LED light source is turned on.  
-"propixxTScopePrepAcknowledge" is 1 if [PROPixx](PROPixx) T-Scope has finished loading  
cover page.  
-"propixxTScopeScheduleFrame" counts [PROPixx](PROPixx) T-Scope stimulus frames.  
-"propixxLedMask" Current mask on the [LEDs](LEDs).  
See [DatapixxStatusDemo](DatapixxStatusDemo) example.  
  


###See also:
[SetVideoMode](Datapixx-SetVideoMode), [SetVideoHorizontalSplit](Datapixx-SetVideoHorizontalSplit), [SetVideoVerticalStereo](Datapixx-SetVideoVerticalStereo)
