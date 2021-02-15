# [SyncedCLUTUpdateTest](SyncedCLUTUpdateTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[SyncedCLUTUpdateTest](SyncedCLUTUpdateTest)([synced=1])  
  
Perceptual test to test synchronization of hardware gamma table  
updates to the vertical refresh and to [Screen](Screen)('[Flip](Flip)').  
  
The command [Screen](Screen)('LoadNormalizedGammaTable') provides the optional parameter  
'loadOnNextFlip'. If set to 1, Psychtoolbox is requested to defer the upload  
of the specified gamma table until next execution of the [Screen](Screen)('[Flip](Flip)') command,  
i.e. swapping the back- and front buffers and update of the gamma table should  
happen synchronously with each other and with vertical retrace.  
  
This test allows to perceptually check correctness of this mechanism. In a loop  
it shows two alternating stimuli: A gray-level ramp of range 0-255, displayed  
with a hardware lut of \*half\* intensity range 0-0.5. Then, after next retrace, a  
gray-level ramp of \*half\* range 0-128 with a hardware lut of \*full\* intensity range  
0-1.0. If update of the visual stimulus (the graylevel ramp) and of the corresponding  
clut happens synchronously at the same vertical retrace during the '[Flip](Flip)' command,  
as expected, then the half intensity stim + full intensity lut or full intensity stim +  
half intensity lut should cancel each other out, resulting in the perception of a  
half-intensity gray-ramp with no or only minimal flicker. If, on the other hand,  
synchronisation of clut update and flip doesn't work properly, then one should see  
a strong flicker of the gray-ramp due to non-matching stimulus and clut.  
  
You can easily produce the visual impression of failed sync by providing the optional  
parameter synced = 0 to enforce non-synced updates.  
  
Even if synced updates work, you may see some artifacts at the top of the display,  
due to the inability of slow gfx-hardware to update the lut quickly enough. Either  
avoid that display area for your stim or buy a faster graphics card. Enabling realtime  
scheduling via [Priority](Priority)() command may also help.  
  
The accuracy of stimulus onset timestamps may be reduced on M$-Windows when using  
this mode of operation.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/SyncedCLUTUpdateTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/SyncedCLUTUpdateTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/SyncedCLUTUpdateTest.m</code>
</div>

