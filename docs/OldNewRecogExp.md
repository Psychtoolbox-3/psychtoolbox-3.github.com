# [OldNewRecogExp](OldNewRecogExp)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[PsychExampleExperiments](PsychExampleExperiments)>[OldNewRecognition](OldNewRecognition)

[OldNewRecogExp](OldNewRecogExp)(subNo,hand);  
  
Example of an old/new recognition experiment.  
  
This is an example of a simple old/new recognition experiment. It is split  
into two phases, a study phase and a test phase:  
  
### Study phase:  
  
In the study phase, the subject is presented with 3 images of objects in  
randomized presentation order and has to learn/memorize them. Each image  
is presented for a 'duration' of 2 seconds, then the image disappears and  
the subject has to advance to the next presentation by pressing the 'n'  
key on the keyboard. The list of 'study' objects is read from the file  
'studylist.txt'.  
  
### Test phase:  
  
In the test phase, the subject is presented with test images defined in  
the file 'testlist.txt', again in randomized order. Test images are  
presented for a 'duration' of 0.5 seconds or until the subjects responds  
with a keypress. The subject has to press one of two keys, telling if the  
test image is an "old" image - previously presented in the study phase,  
or a "new" image - not seen in the study phase. The keys used are 'c' and  
'm', the mapping of keys to response ("old" or "new") is selected by the  
input argument "hand" -- allowing to balance for handedness of subjects /  
response bias.  
  
At the end of a session (when all images in the 'testlist.txt' have been  
presented and tested), the results - both response of the subject and its  
reaction time - are stored to a file 'OldNewRecogExp\_xx.dat', where 'xx'  
is the subject number given as input argument "subNo" to this script.  
  
### Input parameters:  
  
subNo    subject number; use subNo\>99 to skip check for existing file  
hand     response mapping for test phase  
  
e.g.: [OldNewRecogExp](OldNewRecogExp)(99,1);  
  
### Example DESIGN:  
  
STUDY PHASE: study 3 objects  
TEST  PHASE: shown 6 objects, decide whether the object is old or new  
  
### This script demonstrates:  
  
   - reading from files to get condition on each trial  
   - randomizing conditions (for the study and test phase)  
   - showing image/collecting response (response time, accuracy)  
   - writing data to file "[OldNewRecogExp](OldNewRecogExp)\_<subNo\>.dat  
  
Please refer to other included demos for new functions of Psychtoolbox-3  
vs. the old Psychtoolbox-2.  
  
Other than a few changes how to call the [Screen](Screen) function,  
and the try ... catch statements, this code replicates a  
typical OS9 experiment  
  
NOTE to previous [MacOS](MacOS)-9 users: OSX is case sensitive!!!  
  
### History:  
  
05/24/05 Quoc Vuong, [PhD](PhD), University of [NewCastle](NewCastle) wrote and contributed  
it, as an example for usage of Psychtoolbox-3, Version 1.0.6.  
03/01/08 Mario Kleiner modified the code to make use of new functionality  
added in Psychtoolbox 3.0.8.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/PsychExampleExperiments/OldNewRecognition/OldNewRecogExp.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/PsychExampleExperiments/OldNewRecognition/OldNewRecogExp.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/PsychExampleExperiments/OldNewRecognition/OldNewRecogExp.m</code>
</div>

