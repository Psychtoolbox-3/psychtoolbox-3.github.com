# [PsychVideoDelayLoop](PsychVideoDelayLoop)
##### >[Psychtoolbox](Psychtoolbox)>[PsychVideoCapture](PsychVideoCapture)

[PsychVideoDelayLoop](PsychVideoDelayLoop)(subcommand, arg1, arg2, ...)  
  
This implements a realtime video feedback loop with adjustable  
delay, e.g., for action-perception studies.  
  
Arguments:  
subcommand - Is a string containing the subcommand to call.  
arg1, ... argn - Are the arguments that the specific subcommand  
requires.  
  
### Subcommands, their meaning and arguments:  
  
[PsychVideoDelayLoop](PsychVideoDelayLoop)('Verbosity', level);  
-- Set level of verbosity: 0 == Shut up. 1 == Errors and warnings.  
2 == Information as well. The default is 1.  
  
handle = [PsychVideoDelayLoop](PsychVideoDelayLoop)('Open', windowPtr [,deviceId] [,ROI] [,inColor])  
-- Open a video capture device 'deviceId' for use on a specific onscreen  
window 'windowPtr', setup region of interest 'ROI', select if capture  
should happen 'inColor' = 1 or gray-scale (inColor = 0).  
This returns a 'handle' for the device, so other scripts can do  
device specific setup.  
  
[PsychVideoDelayLoop](PsychVideoDelayLoop)('[Close](Close)')  
-- Shutdown, close and release all video capture devices. This  
invalidates any handle obtained from 'Open'.  
  
fps = [PsychVideoDelayLoop](PsychVideoDelayLoop)('TuneVideoRefresh', capturerate)  
-- Measure the exact capture rate of the video device when  
requesting a capturerate of 'capturerate', check if the displays  
refresh rate is roughly compatible with the capture device setting  
and then try to fine-tune the display refresh rate in order to  
minimize phase-shifts between capture device work-cycle and display  
device work-cycle. Return the final fine-tuned and measured framerate  
'fps' of the display device.  
Note: Fine-tuning is only possible in a very narrow range (+/- 1Hz)  
around the display refresh rate set in your display settings. This  
feature is currently only supported on GNU/Linux.  
  
[PsychVideoDelayLoop](PsychVideoDelayLoop)('SetAbortKeys', keyarray)  
-- Define a sequence of keycodes for valid abort  
keys. If any of the keys given in the sequence is pressed, the  
video loop will exit. You can map keys to keycodes via [KbName](KbName), e.g.,  
key1 = [KbName](KbName)('Escape'); key2 = [KbName](KbName)('Space'); keyarray = [key1 key2];  
--\> Create a keyarray that would abort on Escape- or Space- keypress.  
  
[PsychVideoDelayLoop](PsychVideoDelayLoop)('SetAbortTimeout', timeout)  
-- Define a maximum duration of the feedback loop in seconds. After  
that amount of time has elapsed, the loop will exit.  
  
[PsychVideoDelayLoop](PsychVideoDelayLoop)('SetHeadstart', timemargin)  
-- Define an estimate of how long the system will take to process a  
new video frame plus the expected drift during one trial. The loop  
will take this extra amount of time into account when prestarting the  
camera to make sure that the excess latency caused by the video loop itself  
is as short and stable as possible. E.g., a value of 0.004 secs for  
processing overhead + maybe 0.004 secs for drift == 0.008 secs could  
be reasonable for an otherwise well synchronized system.  
  
[PsychVideoDelayLoop](PsychVideoDelayLoop)('SetPresentation', fullfov, mirrored, upsidedown);  
-- Change mode of presentation: fullfov=0 Show centered image, fullfov=1  
Zoom image to fill full area of onscreen window. mirrored=0 Normal  
presentation, mirrored=1 Mirror left-right. upsidedown=0 Upright,  
upsidedown=1 Upside-Down.  
  
[PsychVideoDelayLoop](PsychVideoDelayLoop)('SetLogging', mode, maxseconds)  
-- Disable (mode=0) or enable (mode=1) logging of timestamps.  
'maxseconds' is the number of seconds for which the arrays should  
be pre-allocated. After running the delay loop you can query the  
logged timestamps via the 'GetLog' subfunction.  
  
log = [PsychVideoDelayLoop](PsychVideoDelayLoop)('GetLog')  
-- Return the timing logs of last loop run. This is a 3 rows by  
n columns matrix, where each column corresponds to the timing  
samples of one frame: log(1,i) = Absolute system time in seconds,  
when frame i was captured. log(2,i) = Delta (seconds) between  
capture and visual onset of image i on screen. log(3,i) contains  
an estimate of the full delay between capture onset of frame i and  
visual onset. It is the value log(2,i) + estimated latency between  
start of camera sensor exposure and transmit completion for the frame.  
The accuracy of this estimate should be pretty good for cameras known  
to Psychtoolbox and it is a \*guess\* for the lower bound on the real  
latency on unknown cameras.  
  
[PsychVideoDelayLoop](PsychVideoDelayLoop)('RecordFrames', framestep)  
-- Record every 'framestep'th frame in system RAM as an [OpenGL](OpenGL)  
texture. The video loop doesn't discard every texture after drawing  
it, but enqueues it an a system RAM buffer. The vector of texture  
handles can be retrieved via 'GetRecordedFrames' after the loop  
has finished. Default is zero == Recording disabled. A value of  
one records every frame, a value of two every second, ...  
  
Calling this function will also reset the vector of recorded frames  
to empty, but it will not delete the textures! That is your task.  
  
texids = [PsychVideoDelayLoop](PsychVideoDelayLoop)('GetRecordedFrames')  
Return vector of texture handles for all recorded frames.  
texids(1,i) contains the texture handle for the i'th recorded frame.  
texids(2,i) contains the onset timestamp for the i'th recorded frame.  
  
[PsychVideoDelayLoop](PsychVideoDelayLoop)('RunLoop', delayFrames[, onlinecontrol]);  
-- Run the video feedback loop, using the parameters specified above.  
The video loop will start and run until one of the abort keys is pressed,  
or the timeout is reached. It will log timestamps as requested. Each  
captured video frame is output again after 'delayFrames' capture cycle  
durations, e.g., capturerate = 30 fps -\> cycle = 1/30 sec = 33.33 ms --\>  
delay is at least delayFrames \* 33.33 ms. Images are drawn and shown  
in sync with vertical retrace after that amount of time. The real onset  
time obviously depends on the monitor refresh interval and phase between  
camera and monitor.  
  
If 'onlinecontrol' is set to 1, then a few control keys are enabled to  
allow for interactive change of settings like brightness, gain and  
exposure time: 'b' increases brightness, 'd' decreases brightness.  
Up/[DownArrow](DownArrow) keys increase/decrease gain. Right/[LeftArrow](LeftArrow) keys  
increase/decrease exposure time (shutter time).  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychVideoCapture/PsychVideoDelayLoop.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychVideoCapture/PsychVideoDelayLoop.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychVideoCapture/PsychVideoDelayLoop.m</code>
</div>

