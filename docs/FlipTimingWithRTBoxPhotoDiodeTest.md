# [FlipTimingWithRTBoxPhotoDiodeTest](FlipTimingWithRTBoxPhotoDiodeTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[FlipTimingWithRTBoxPhotoDiodeTest](FlipTimingWithRTBoxPhotoDiodeTest)([configFile][, targetFolder][, usevulkan=0][, bpc=8])  
  
Test visual stimulus onset timing accuracy and visual stimulus onset  
timestamping precision and robustness under varying loads, conditions and  
modes of operation. This requires one of the supported external  
measurement devices to provide the "ground truth" for true stimulus onset  
times. Currently supported:  
- UCST [RTBox](RTBox) with its own photo-diode (p)  
- [VPixx](VPixx) Inc. [DataPixx](DataPixx)/[ViewPixx](ViewPixx)/[ProPixx](ProPixx) (d)  
- UBW32/Bitwhacker + UCST [VideoSwitcher](VideoSwitcher) (b)  
- UCST Videoswitcher + UCST [RtBox](RtBox) or CRS Bits\# emulated [RtBox](RtBox) (v)  
- Other TTL trigger timestamp emitting devices + UCST [RtBox](RtBox) or CRS Bits\#,  
  e.g., the CRS-[ColorCal2](ColorCal2) used as a photo-diode. (p)  
  
The script can also be used without external equipment (n) to just test  
stimulus onset accuracy with only indirect test of timestamping.  
  
This documentation is incomplete for now, good luck!  
  
'configFile' Filename of benchmark configuration file. If none is specified,  
the file fliptimingdefaultconfig.mat from the Psychtoolbox/[PsychTests](PsychTests)/[TestConfigurations](TestConfigurations)/  
folder is used for some reasonable default testing setup.  
  
'targetFolder' Target folder for result files. If none is specified, a reasonable  
location is selected if that location exists and is writable, if that does not work,  
a fallback location is selected, if that does not work, the users home directory is  
selected. If a folder is specified, that folder is used if it is writable, otherwise  
the users home directory is tried as target.  
  
'usevulkan' If 1, try to use a Vulkan display backend instead of the  
[OpenGL](OpenGL) display backend. See 'help PsychVulkan' for supported hardware +  
operating system combinations and required setup.  
  
'bpc' Request a specific output framebuffer color precision. Currently  
supported are 8 for standard 8 bpc RGBA8 framebuffer, 10 bpc for RGB10A2,  
and 16 bpc for a RGBA16F floating point framebuffer. Defaults to 8 bpc,  
which is the only precision that is guaranteed to be supported on all  
operating systems, graphics cards and displays.  
  
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

