# [Eyelink('DriftCorrStart')](Eyelink-DriftCorrStart) 
##### [Psychtoolbox](Psychtoolbox)>[Eyelink](Eyelink).{mex*} subfunction


Start drift correction, specify target position with x and y.  
If the optional 'dtype' argument is zero, the routine eyelink\_driftcorr\_start()  
is called. If 'dtype' is one, do\_drift\_correct() is called. In that case, the  
argument 'dodraw' selects if Eyelink itself should draw the target (1), or if it  
is left to usercode. 'allow\_setup' if set to 1, will allow eyelink to enter the  
setup menu if [ESCape](ESCape) key is pressed. Otherwise, eyelink will terminate a running  
drift correction on press of the [ESCape](ESCape) key.  
  


###See also:

