# [SoundTrigger](SoundTrigger)
##### >[Psychtoolbox](Psychtoolbox)>[PsychObsolete](PsychObsolete)

Basic test and demo of the sound recording/capture functionality of the  
new [PsychSound](PsychSound)() function.  
  
Parameters: duration = Recordingcapacity (in seconds) of the sound capture  
buffer. After recording of sound has been started, [PsychSound](PsychSound) will  
perform continuous recording into an internal ring-buffer with a storage capacity  
of 'duration' seconds, until recording gets stopped again. Soundrecording  
is done asynchronously as an automatic background process, independent of  
Matlabs/Psychtoolboxs execution. This way you can continue execution of  
your Matlab script (sound output, response collection, visual output,  
...) while [PsychSound](PsychSound) is recording in the background. You can query the  
amount of new recorded sound data in the buffer and you can fetch this  
data from the buffer into a Matlab matrix at any time during of after  
recording. Be aware though that if the buffers capacity is exhausted, it  
will dispose old sound data to store new one - only the last 'duration'  
seconds of the most recently recorded sound are kept.  
  
### This leaves you with two options:  
  
a) Request a buffer big enough to store the full duration of your  
recording from Start of capture until the end, and read out the recorded  
data into a Matlab matrix after the end of the recording. This is the  
most easy to implement (nice linear control flow Start-\>Stop-\>Fetch), but  
you have to know the maximum duration in advance, and you'll potentially  
use up significant amounts of memory.  
  
b) Request a buffer big enough to hold sound data for at least the  
duration of one iteration of your trial loop. During each iteration, poll  
and fetch portions of the recording into your Matlab matrix. More  
involved programming, but low memory consumption.  
  
With b) you can obviously also implement an audio recorder for infinite  
capture into a file via while(1) Waitabit; Poll&Fetch bit of sound data  
from [PsychSound](PsychSound) into Matrix; Append content of matrix to a file; end;  
  
And you can do live capture, manipulation & analysis of sound, e.g.,  
voice triggers, feedback of recorded sound to sound output and such.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychObsolete/SoundTrigger.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychObsolete/SoundTrigger.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychObsolete/SoundTrigger.m</code>
</div>

