# [Datapixx('EnableVideoLcd3D60Hz')](Datapixx-EnableVideoLcd3D60Hz) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Liquid crystal displays can exhibit an artifact when presenting 2 static images  
on alternating video frames, such as with frame-sequencial 3D. The origin of  
this artifact is related to LCD pixel polarity inversion. The optical  
transmission of a liquid crystal cell varies with the magnitude of the voltage  
applied to the cell. Liquid crystal cells are designed to be driven by an AC  
voltage with little or no DC component. As such, the cell drivers alternate the  
polarity of the cell's driving voltage on alternate video frames. The cell will  
see no net DC driving voltage, as long as the pixel is programmed to the same  
intensity on even and odd video frames. Small differences in a pixel's even and  
odd frame luminance tend to leave the cell unaffected, and large differences in  
even and odd frame luminance for short periods of time (10-20 frames?) also do  
not seem to affect the cell; however, large differences in luminance for a  
longer period of time will cause a DC buildup in the pixel's liquid crystal  
cell. This can result in the pixel not showing the programmed luminance  
correctly, and can also cause the pixel to "stick" for several seconds after the  
image has been removed, causing an after-image on the display. [VPixx](VPixx)  
Technologies has developed a strategy for keeping the pixel cells DC balanced.  
Instead of alternating the cell driving voltage on every video frame, we can  
alternate the voltage only on every second frame. This feature is enabled by  
calling this routine. Call this routine before presenting static or  
slowly-moving 3D images, or when presenting 60Hz flickering stimuli. Be sure to  
call [DisableVideoLcd3D60Hz](DisableVideoLcd3D60Hz) afterwards to return to normal pixel driving. Note  
that this feature is only supported on the [VIEWPixx](VIEWPixx)/3D when running with a  
refresh rate of 120Hz.  
  


###See also:
[DisableVideoLcd3D60Hz](Datapixx-DisableVideoLcd3D60Hz)
