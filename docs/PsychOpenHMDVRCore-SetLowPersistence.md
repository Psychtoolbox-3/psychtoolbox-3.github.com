# [PsychOpenHMDVRCore('SetLowPersistence')](PsychOpenHMDVRCore-SetLowPersistence) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenHMDVRCore](PsychOpenHMDVRCore).{mex*} subfunction

oldPersistence = PsychOpenHMDVRCore('SetLowPersistence', openhmdPtr [, lowPersistence]);

Enable or disable low persistence mode on display panel of [OpenHMD](OpenHMD) device  
'openhmdPtr'.  
DOES NOTHING AT THE MOMENT!  
'lowPersistence' 1 = Enable low persistence, 0 = Disable low persistence.  
In low persistence mode, the pixels will only light up for a fraction of a video  
refresh duration, thereby reducing motion blur due to smooth pursuit eye  
movements or other shuttering effects. Brightness of the display will be reduced  
though, and flicker sensitive people may perceive more flicker.  
Returns previous 'oldPersistence' setting.  
  


###See also:

