# [PsychGPUControl](PsychGPUControl)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[rc,rcExt] = [PsychGPUControl](PsychGPUControl)(cmd, arg); -- Control low-level GPU settings.  
  
[PsychGPUControl](PsychGPUControl) calls into external helper tools to change certain  
low-level operating settings of your systems graphics card (GPU).  
  
Not all operating systems and GPU's support this. The function will  
do nothing on unsupported OS/GPU combos.  
  
Currently OS/X doesn't support this function at all, and on MS-Windows  
and GNU/Linux, only recent ATI GPU's with recent drivers do support it.  
  
All subfunctions return an optional 'rc' return code of zero on success,  
non-zero on error or if the feature is unsupported.  
'rcExt' is optional as well and its meaning depends on the subfunction.  
  
### Subfunctions and their syntax & meaning:  
  
[rc,rcExt] = [PsychGPUControl](PsychGPUControl)('SetDitheringEnabled', enableFlag);  
- Depending on the setting of 'enableFlag', either enable (=1) or  
disable (=0) display color dithering on all connected displays.  
'rcExt' returns the version of the low-level dithering API (currently 1 or 2)   
that had to be used in order to overcome compatibility issues (Windows/AMD   
only). 'rcExt' is only non-empty when the API was reported by the low-level  
function.  
  
Under normal circumstances, the GPU should decide itself if dithering  
should be used or not. This function allows you to override the GPU's  
automatic choice.  
  
rc = [PsychGPUControl](PsychGPUControl)('SetGPUPerformance', gpuPerformance);  
- Select the performance state of the GPU. 'gpuPerformance' can be set to  
0 if the GPU shall automatically adjust its performance and power-  
consumption, or to one of 10 fixed levels between 1 and 10, where 1 means  
the lowest performance - and power consumption, whereas 10 means the  
highest performance - and maximum power consumption.  
  
If in doubt, choose 10 for best accuracy of visual stimulus onset timing,  
0 for non-critical activities to leave the decision up to the graphics  
driver and GPU.  
  
  
rc = [PsychGPUControl](PsychGPUControl)('FullScreenWindowDisablesCompositor', flag [, screenIds]);  
- Select if desktop composition should be disabled for displays where  
a Psychtoolbox fullscreen onscreen window is displayed. 'flag' == 1 means  
to disable composition for fullscreen windows, 0 means to enable composition  
for fullscreen windows. You usually want composition to be disabled, as this  
is currently the only way to get decent timing and precise visual stimulus  
onset timestamping. The optional vector of 'screenIds' selects which screens  
should be affected by the change. If left out or set to [], all detected  
screens will be changed. This will also apply a workaround for a limitation in  
Ubuntu Linux standard Unity GUI (actually in the Compiz compositor) when used on  
a single-x-screen setup with multiple video outputs, e.g., a single x-screen,  
dual-display stereo setup. For the workaround to work, you may have to logout  
and login again once, as sometimes the system does not seem to pick up the new  
settings until a logout/login cycle.  
  
  
rc = [PsychGPUControl](PsychGPUControl)('EnableCompizMultiDisplayWorkaround', enableFlag);  
- Enable or disable workaround for a limitation of the Ubuntu Linux Unity GUI  
if one wants to do multi-display visual stimulation on a single x-screen setup  
or on X-[Screen](Screen) 0 of a multi x-screen setup. Trying to open a Psychtoolbox  
fullscreen window on PTB screen 0 aka X-[Screen](Screen) 0 if that X-[Screen](Screen) has multiple  
active displays attached, e.g., for dual-display stereo stimulation, can fail  
to work without severe visual stimulation timing problems. This is due to a  
design limitation of Unity's Compiz desktop compositor, as of Ubuntu 16.04.0 LTS  
and earlier distribution versions. You can either solve this problem by switching  
to a different desktop GUI environment like GNOME-3 or KDE, or by attaching all  
visual stimulation displays to a secondary X-[Screen](Screen), e.g., screen 1 (run [XOrgConfCreator](XOrgConfCreator)  
to set up such a setup). If you want to use Unity, you can use this function to  
enable a workaround that fixes the problem, either immediately or after a logout  
and login. There are no known downsides of the workaround when using your system  
with a single display attached. The downside of the workaround on multi-display  
setups will be that while Psychtoolbox will work fine, during your regular use of  
the desktop GUI, automatic window placement and resizing of regular GUI applications  
may be suboptimal due to the workaround interfering. Windows will no longer maximize  
on a single display screen if you ask them to, but over the whole desktop. You can  
use this function to enable and disable the workaround if you tend to use your desktop  
not only for multi-display stimulation, but also for regular multi-display desktop use.  
  
Set 'enableFlag' to 1 to enable the workaround for visual stimulation, and 0  
to disable the workaround for more ergonomic multi-display desktop use.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/PsychGPUControl.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/PsychGPUControl.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/PsychGPUControl.m</code>
</div>

