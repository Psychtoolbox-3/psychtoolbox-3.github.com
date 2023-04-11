# [CV1Test](CV1Test)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PsychVRToolbox](PsychVRToolbox)

res = [CV1Test](CV1Test)([waitframes=90][, useRTbox=0]) - A timing test script for [HMDs](HMDs) by use of a photometer.  
  
Needs the [RTBox](RTBox), and a photo-diode or such, e.g., a [ColorCal](ColorCal)-II,  
connected to the TTL trigger input of a [RTBox](RTBox) or CRS Bits\#.  
  
While measured timestamps/timing on [OculusVR](OculusVR)-1 via [PsychOculusVR1](PsychOculusVR1) is catastrophic,  
and bad on all proprietary [OpenXR](OpenXR) runtimes on Windows [(OculusVR]((OculusVR), [SteamVR)](SteamVR)) and Linux  
[(SteamVR)]((SteamVR)), as well as with standard Monado, we get close to perfect timestamps with  
our "metrics enhanced" Monado on Linux + Mesa Vulkan drivers with timestamping support,  
as tested with both Oculus Rift CV-1 and HTC Vive Pro Eye on AMD Raven Ridge apu with  
radv + timing extension and Monado metrics mode. Errors are sub-millisecond wrt. to  
testing with a [ColorCal2](ColorCal2) and also with a Videoswitcher in simulated HMD mode.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/CV1Test.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/CV1Test.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychVRToolbox/CV1Test.m</code>
</div>

