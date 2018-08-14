# [PsychGPUTestAndTweakGammaTables](PsychGPUTestAndTweakGammaTables)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

  
[PsychGPUTestAndTweakGammaTables](PsychGPUTestAndTweakGammaTables) - Test and tweak GPU hardware gamma tables.  
  
This function is a helper function used for high-precision display  
devices like the Bits\# from CRS and [DataPixx](DataPixx)/[ViewPixx](ViewPixx)/[ProPixx](ProPixx) from [VPixx](VPixx),  
which need identity passthrough of framebuffer pixel data to the video outputs  
without any interference by the GPU and other intermediate encoder circuitry.  
  
It augments functions like [LoadIdentityClut](LoadIdentityClut), trying to cope with [GPUs](GPUs) that  
are too broken to be fixable just by that function without any actual  
measurement of video signals.  
The function is called by toolboxes for special display output hardware  
and makes use of / calls back into hardware specific functions of that  
hardware to allow an iterative feedback loop of parameter tweaks and  
measurements to execute in order to optimize gamma tables for optimal  
pixel passthrough after other hardware-independent measures have failed.  
  
The routine is, e.g., used by the 'GPUEncoderTest' / 'CheckGPUSanity'  
functions of the [PsychDatapixx](PsychDatapixx) and [BitsPlusPlus](BitsPlusPlus) functions.  
  
Input parameters: (Mandatory)  
'win' = Onscreen window handle for onscreen window which displays to the  
        external high precision display device.  
  
'deviceType' = Type of device: 0 = [VPixx](VPixx) Inc. Data-/View-/Pro-Pixx.  
                               1 = CRS Bits\#  
  
'injectFault' = 1 = Intentionally setup a slightly faulty LUT to perturb  
                the signal and test the tweaking procedure. 0 = Don't.  
  
Returns 0 on success, 1 on failure.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychGPUTestAndTweakGammaTables.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychGPUTestAndTweakGammaTables.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychGPUTestAndTweakGammaTables.m</code>
</div>

