# [FlipTimingWithRTBoxPhotoDiodeTest](FlipTimingWithRTBoxPhotoDiodeTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[FlipTimingWithRTBoxPhotoDiodeTest](FlipTimingWithRTBoxPhotoDiodeTest)([configFile][, targetFolder])  
  
Test visual stimulus onset timing accuracy and visual stimulus onset  
timestamping precision and robustness under varying loads, conditions and  
modes of operation. This requires one of the supported external  
measurement devices to provide the "ground truth" for true stimulus onset  
times. Currently supported: UCST [RTBox](RTBox) with photo-diode, [VPixx](VPixx) Inc. [DataPixx](DataPixx)/  
[ViewPixx](ViewPixx)/[ProPixx](ProPixx), UBW32/Bitwhacker + UCST [VideoSwitcher](VideoSwitcher). The script can also  
be used without external equipment to just test stimulus onset accuracy with  
only indirect test of timestamping.  
  
This documentation is incomplete for now, good luck!  
  
'configFile' Filename of benchmark configuration file. If none is specified,  
the file fliptimingdefaultconfig.mat from the Psychtoolbox/[PsychTests](PsychTests)/[TestConfigurations](TestConfigurations)/  
folder is used for some reasonable default testing setup.  
  
'targetFolder' Target folder for result files. If none is specified, a reasonable  
location is selected if that location exists and is writable, if that does not work,  
a fallback location is selected, if that does not work, the users home directory is  
selected. If a folder is specified, that folder is used if it is writable, otherwise  
the users home directory is tried as target.  
  
# Mandatory variables in the config file, part of the struct variable 'conf'  
  
conf.Stereo              = Stereomode to use.  
conf.[Priority](Priority)            = Realtime priority to use.  
conf.[DWMEnabled](DWMEnabled)          = 1,0,-1 = On, Off, Auto  
conf.[SetForegroundWindow](SetForegroundWindow) = 1,0,-1 = On, Off, Auto  
conf.[VBLTimestampingMode](VBLTimestampingMode) = Mode of high-precision timestamping.  
conf.[CheckAsyncFlip](CheckAsyncFlip)      = 0,1,2 = Off-Use sync flip, 1 = Use async flip, 2 = Use async flip with polling, 3 = Use async flip with Waituntilasyncflipcertain.  
  
### Per trial parameters for trial i:  
  
conf.waitFramesSched(i)  = Number of ifi's to wait before onset in trial i.  
conf.loadjitter(i)       = Max. random cpu load jitter to apply in frame i.  
conf.gpuLoad(i)          = Number of rects to draw in frame i (GPU load)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/FlipTimingWithRTBoxPhotoDiodeTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/FlipTimingWithRTBoxPhotoDiodeTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/FlipTimingWithRTBoxPhotoDiodeTest.m</code>
</div>

