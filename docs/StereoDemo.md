# [StereoDemo](StereoDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[StereoDemo](StereoDemo)(stereoMode)  
  
Demo on how to use [OpenGL](OpenGL)-Psychtoolbox to present stereoscopic stimuli.  
  
### DEPRECATED! THIS DEMO ONLY DEMONSTRATES THE LEGACY STEREO SUPPORT!  
If you have a recent graphics card, have a look at [ImagingStereoDemo](ImagingStereoDemo).m  
instead. It demonstrates a much better, more flexible, robust way of  
presenting stereo stimuli with Psychtoolbox.  
  
  
Press any key to abort demo any time.  
  
### stereoMode specifies the type of stereo display algorithm to use:  
  
0 == Mono display - No stereo at all.  
  
1 == [Flip](Flip) frame stereo (temporally interleaved) - You'll need shutter  
glasses that are supported by the operating system, e.g., the  
[CrystalEyes](CrystalEyes)-Shutterglasses.  
  
2 == Top/bottom image stereo with lefteye=top also for use with special  
[CrystalEyes](CrystalEyes)-hardware.  
  
3 == Same, but with lefteye=bottom.  
  
4 == Free fusion (lefteye=left, righteye=right): This - together wit a  
screenid of zero - is what you'll want to use on MS-Windows dual-display  
setups for stereo output.  
  
5 == Cross fusion (lefteye=right ...)  
  
### 6-9 == Different modes of anaglyph stereo for color filter glasses:  
  
6 == Red-Green  
7 == Green-Red  
8 == Red-Blue  
9 == Blue-Red  
  
10 == Dual-Window stereo: Open two onscreen windows, first one will  
display left-eye view, 2nd one right-eye view. Direct all drawing and  
flip commands to the first window, PTB will take care of the rest. This  
mode is mostly useful for dual-display stereo on [MacOS](MacOS)/X. It only works  
on reasonably modern graphics hardware, will abort with an error on  
unsupported hardware.  
  
11 == Like mode 1 (frame-sequential) but using [Screen](Screen)'s built-in method,  
instead of the native method supported by your graphics card.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/StereoDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/StereoDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/StereoDemo.m</code>
</div>

