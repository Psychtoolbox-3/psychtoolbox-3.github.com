# [kPsychExternalDisplayMethod](kPsychExternalDisplayMethod)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

kPsychExternalDisplayMethod -- Create onscreen window not used for actual visual stimulation.  
  
This flag can be passed to the optional 'specialFlags' parameter of  
[Screen](Screen)('OpenWindow', ...) or [PsychImaging](PsychImaging)('OpenWindow', ...).  
  
It will cause the onscreen window to be marked as not used for actual  
visual stimulation of the subject. Instead some mechanism external to  
[Screen](Screen)() is used for displaying actual stimuli to the test subject. This  
could be a display window driven by the Vulkan/WSI display backend on  
suitable system setups, or some special purpose display hardware with its  
own display SDK, or some VR compositor for certain VR/AR headsets.  
  
This tells [Screen](Screen)() that certain aspects of this window do not matter  
very much, e.g., timing precision, color/contrast precision, etc.,  
because some other entity is responsible to ensure those properties for  
all visual stimuli drawn into this onscreen window, e.g., an external  
VR driver or our [PsychVulkan](PsychVulkan) driver.  
  
In practice this means that [Screen](Screen)() can skip certain - otherwise  
essential - calibrations and startup checks, runtime checks, and various  
warning or status messages during startup or runtime of a session,  
because the calibrations are not needed for performing properly and  
failing those checks or calibrations won't matter at all for the success  
of the session, or the status/warning messages would be nothing more than  
distracting or misleading clutter to the experimenter.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/kPsychExternalDisplayMethod.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/kPsychExternalDisplayMethod.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/kPsychExternalDisplayMethod.m</code>
</div>

