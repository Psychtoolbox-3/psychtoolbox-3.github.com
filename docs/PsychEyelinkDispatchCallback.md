# [PsychEyelinkDispatchCallback](PsychEyelinkDispatchCallback)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkBasic](EyelinkBasic)

[PsychEyelinkDispatchCallback](PsychEyelinkDispatchCallback) implementes the [EyeLink](EyeLink) Core Graphics part  
of the [EyeLink](EyeLink) API. This "Core Graphics" part of our API is responsible  
for handling the times when the API and Host PC takes control of the eye  
tracking procedures. This includes the functionality to stream camera  
images during camera/participant setup, displaying targets at locations  
on the participant screen during calibration, validation, and drift/check  
and correction routines. Complimentary to handling the visual aspect of  
these operations contingent on display routines, the functionality  
implemented herewith also handles the playback of feedback sounds to  
the experimenter and participant for guiding these interactive  
procedures. During these modes of operation, this function also  
implements the forwarding of kepresses to the Host PC that are registered  
on the computer's keyboard which is running this implementation. The  
purpose of this is to make sure that bost Host and Display [PCs](PCs) are  
operating as identically in these modes of operation.  
  
  
This function is normally called from within the Eyelink() mex file.  
Normal user code only calls it once to supply the eyelink defaults struct.  
This is handled within the [EyelinkInitDefaults](EyelinkInitDefaults).m file, so you generally  
should not have to worry about this. However, if you change settings in  
the el structure, you may need to call it yourself.  
  
To define which onscreen window the eye image should be  
drawn to, call it with the return value from [EyelinkInitDefaults](EyelinkInitDefaults), e.g.,  
w=[Screen](Screen)('OpenWindow', ...);  
el=[EyelinkInitDefaults](EyelinkInitDefaults)(w);  
myEyelinkDispatchCallback(el);  
  
  
To actually receive and display the images, register this function as  
eyelink's callback:  
  
  
if Eyelink('Initialize', 'myEyelinkDispatchCallback') ~=0  
      error('eyelink failed init')  
end  
result = Eyelink('StartSetup',1) %put the tracker into a mode capable of sending images  
  
  
then you must hit 'return' on the PTB computer, this key command will be  
sent to the tracker host to initiate sending of images.  
  
  
History:  
15. 3.2009    Derived from [MemoryBuffer2TextureDemo](MemoryBuffer2TextureDemo).m (MK).  
 4. 4.2009    Updated to use [EyelinkGetKey](EyelinkGetKey) + fixed eyelinktex persistence  
                  crash (edf).  
11. 4.2009    Cleaned up. Should be ready for 1st release, although still  
                  pretty alpha quality. (MK).  
15. 6.2010    Added some drawing routines to get standard behaviour back.  
                  Enabled use of the callback by default. Clarified in  
                  helptext that user normally should not have to worry  
                  about calling this file. (fwc)  
20. 7.2010    Drawing of instructions, eye-image+title, playing sounds in  
                  seperate functions  
  
 1. 2.2010    Modified to allow for cross hair and fix bugs. (nj)=  
29.10.2018    Drop 'DrawDots' for calibration target. Some white-space fixes.  
24. 3.2020    Cleaned up the documentation of this function, and added  
                  additiontal handling for two types of stereoscopic  
                  calibrations, ability to reference video files for  
                  animated calibration targets, bug fixes for audio  
                  feedback playback. Apologies to NJ for removing  
                  previous comments where code was previously added, this  
                  was done for easier reading of the code.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/PsychEyelinkDispatchCallback.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/PsychEyelinkDispatchCallback.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/PsychEyelinkDispatchCallback.m</code>
</div>

