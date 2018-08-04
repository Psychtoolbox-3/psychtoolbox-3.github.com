# [PR705config](PR705config)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PR705Toolbox](PR705Toolbox)

[PR705config](PR705config) - Update the PR-705 configuration.  
  
Syntax:  
config\_str (string) = [PR705config](PR705config)  
errcode (scalar) = [PR705config](PR705config)('Option1', value1, 'Option2', value2, ...)  
  
Description:  
A wrapper for setting various options on the PR-705 using the 'S'  
command. With no input arguments, the function merely returns the device's  
current configuration string. In the multiple input arguments case, here  
are the case-insensitive options and the values they take:  
Lens         ID Number of PRIMARY accessory  
Add1         ID Number of 1st ADD ON accessory  
Add2         ID Number of 2nd ADD ON accessory  
Aperture     ID Number of Aperture  
Units        0 for English  
             1 for Metric  
[ExposureTime](ExposureTime) 0 - Adaptive  
             25 ... 60000 ms  
[CaptureMode](CaptureMode)  0 - Single Capture  
             1 - Continuous Capture  
Cycles       1 .. 99 - Number of Captures to average  
[CalcMode](CalcMode)     0 - Power  
             1 - Energy  
[TriggerMode](TriggerMode)  0 - Manual  
             1 - External  
[ViewShutter](ViewShutter)  0 - Open During Measurement  
             1 - Closed During Measurement  
[CIEObserver](CIEObserver)  0 -  2 Degree  
             1 - 10 Degree  
  
Example:  
errcode = [PR705config](PR705config)('Lens', 0, 'Units', 1, 'Cycles', 2, 'ViewShutter', 1);  
  
12/06/12    zlb   Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PR705Toolbox/PR705config.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PR705Toolbox/PR705config.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PR705Toolbox/PR705config.m</code>
</div>

