# [PsychPortAudioDataPixxTimingTest](PsychPortAudioDataPixxTimingTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[PsychPortAudioDataPixxTimingTest](PsychPortAudioDataPixxTimingTest)([waitTime = 1][, exactstart=1][, deviceid=-1][, latbias=0][, triggerLevel=0.01][, reqlatencyclass=2])  
  
Test script for sound onset timing reliability and sound onset latency of  
the [PsychPortAudio](PsychPortAudio) sound driver.  
  
This script configures the driver for low latency and high timing  
precision, then executes ten trials where it tries to emit a beep sound,  
starting in exact sync to a black-white transition on the display.  
  
You'll need measurement equipment to use this: A [DataPixx](DataPixx) device from  
[VPixx](VPixx) technologies, connected to your computer via the USB connection  
cable. Also a connection between the line-out jack of your soundcard and  
the line-in jack of the [DataPixx](DataPixx) to transmit the sound data. The [DataPixx](DataPixx)  
will receive the audio output of [PsychPortAudio](PsychPortAudio)/Your Soundcard, timestamp  
it and send the computed timing data to your computer via USB.  
  
Some parameters may need tweaking, especially the 'triggerLevel'  
parameter.  
  
### Optional parameters:  
  
'waitTime'   = Time to wait (in seconds) before playing sound. Defaults  
               to 1 second if omitted.  
  
'exactstart' = 0 -- Start immediately, measure absolute latency.  
             = 1 -- Test accuracy of scheduled sound onset. (Default)  
  
'deviceid'   = -1 -- Auto-select optimal device (Default).  
            \>=0   -- Select specified output device. See  
                     [PsychPortAudio](PsychPortAudio)('GetDevices') for a list of devices.  
  
'latbias'    = Hardware inherent latency bias. To be determined by  
               measurement - allows to PA to correct for it if provided.  
               Unit is seconds. Defaults to zero.  
  
'triggerLevel' = Sound signal amplitude for [DataPixx](DataPixx) to detect sound  
                 onset. Defaults to 0.01 = 1% of max amplitude if  
                 exactstart == 0, otherwise it is auto-detected by  
                 calibration. This will likely need tweaking on your  
                 setup.  
  
'reqlatencyclass' Override setting for reqlatencyclass parameter. By default,  
                  reqlatencyclass = 2 is used, for exclusive device access for  
                  low latency / high timing precision mode.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/PsychPortAudioDataPixxTimingTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/PsychPortAudioDataPixxTimingTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/PsychPortAudioDataPixxTimingTest.m</code>
</div>

