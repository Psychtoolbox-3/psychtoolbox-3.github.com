# [MakeTextureTimingTest](MakeTextureTimingTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[MakeTextureTimingTest](MakeTextureTimingTest)  
  
[Screen](Screen) 'MakeTexture' both allocates memory to hold an [OpenGL](OpenGL) texture and  
loads a MATLAB matrix into the [OpenGL](OpenGL) texture. [TestMakeTextureTiming](TestMakeTextureTiming)  
times those two steps separately, reporting the fraction of time which  
[MakeTexture](MakeTexture) spends allocating memory.     
  
On 1GHz G4, [MakeTexture](MakeTexture) spends less than 3% of its time allocating memory.  
Providing separate [Screen](Screen) subfuntions to allocate and fill textures would  
gain little.  
  
see also: [PsychTests](PsychTests)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/MakeTextureTimingTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/MakeTextureTimingTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/MakeTextureTimingTest.m</code>
</div>

