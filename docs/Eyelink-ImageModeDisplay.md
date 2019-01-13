# [Eyelink('ImageModeDisplay')](Eyelink-ImageModeDisplay) 
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink).{mex*} subfunction


This handles display of the [EyeLink](EyeLink) camera images. While in imaging mode, it  
continuously requests and displays the current camera image. It also displays  
the camera name and threshold setting. Keys on the subject PC keyboard are sent  
to the tracker so the experimenter can use it during setup. It will exit when  
the tracker leaves imaging mode or disconnects. RETURNS: 0 if OK, 32767 [(Ox7FFF]((Ox7FFF)  
or TERMINATE\_KEY) if pressed, -1 if disconnect  


###See also:

