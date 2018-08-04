# [EyeLinkPicture](EyeLinkPicture)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkDemos](EyelinkDemos)>[SR-ResearchDemo](SR-ResearchDemo)

 Short MATLAB example that uses the Eyelink and Psychophysics Toolboxes  
 This is the example as shown in the [EyelinkToolbox](EyelinkToolbox) article in BRMIC  
 Cornelissen, Peters and Palmer 2002), but updated to also work on the  
 PC version of the toolbox, and uses some new routines.  
  
 Adapted after "Psychtoolbox\[PsychHardware](PsychHardware)\[EyelinkToolbox](EyelinkToolbox)\[EyelinkDemos](EyelinkDemos)\  
 [ShortDemos](ShortDemos)\[EyelinkExample](EyelinkExample).m"  
  
###  HISTORY  
  
 mm/dd/yy  
 07/01/08 js    redone the structure of the experiment and added   
        integration messages to the [EyeLink](EyeLink) Data Viewer software  
 07/14/08 js    added code to set your own EDF file name before opening  
        the experiment graphics  
 07/13/10  fwc made to work with new toolbox with callback and updated to  
               enable eye image display, added "cleanup" function,  
               reenabled try-catch  
 09/20/12 srresearch updated to allow:  
               1. Transfer the image to host. (STEP 7.1)  
               2. Change the calibration colors and turn on/off the  
                   calibration beep. (STEP 6)  
               3. End trials by button box. (STEP 7.5)  
 12/20/13  srresearch  
                Added part to make it run with octave  
                fixed issue with non integer arguments for Eyelink('message' ...)  
                removed cleanup function, used Eyelink('ShutDown'); [Screen](Screen)('CloseAll') instead.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemo/EyeLinkPicture.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemo/EyeLinkPicture.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemo/EyeLinkPicture.m</code>
</div>

