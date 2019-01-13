# [PsychEyelinkDispatchCallback](PsychEyelinkDispatchCallback)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkBasic](EyelinkBasic)

Retrieve live eye-image from Eyelink, show it in onscreen window.  
  
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
  
  
to actually receive and display the images, register this function as eyelink's callback:  
if Eyelink('Initialize', 'myEyelinkDispatchCallback') ~=0  
  error('eyelink failed init')  
end  
result = Eyelink('StartSetup',1) %put the tracker into a mode capable of sending images  
then you must hit 'return' on the PTB computer, this key command will be sent to the tracker host to initiate sending of images.  
  
This function fetches the most recent live image from the Eylink eye  
camera and displays it in the previously assigned onscreen window.  
  
History:  
15.3.2009   Derived from [MemoryBuffer2TextureDemo](MemoryBuffer2TextureDemo).m (MK).  
 4.4.2009   Updated to use [EyelinkGetKey](EyelinkGetKey) + fixed eyelinktex persistence crash (edf).  
11.4.2009   Cleaned up. Should be ready for 1st release, although still  
            pretty alpha quality. (MK).  
15.6.2010   Added some drawing routines to get standard behaviour back. Enabled  
            use of the callback by default. Clarified in helptext that user  
            normally should not have to worry about calling this file. (fwc)  
20.7.2010   drawing of instructions, eye-image+title, playing sounds in seperate functions  
  
 1.2.2010   modified to allow for cross hair and fix bugs. (nj)  
29.10.2018  Drop 'DrawDots' for calibration target. Some white-space fixes.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/PsychEyelinkDispatchCallback.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/PsychEyelinkDispatchCallback.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/PsychEyelinkDispatchCallback.m</code>
</div>

