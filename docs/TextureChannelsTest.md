# [TextureChannelsTest](TextureChannelsTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[TextureChannelsTest](TextureChannelsTest)  
  
Test proper assignment of matrix layers to RGBA texture channels.  
  
### What you should see during the test:  
  
1. A red square on a black background. Keypress!  
2. A green square on a black background. Keypress!  
3. A blue square on a black background. Keypress!  
4. A black screen. Keypress!  
End.  
  
If you see different colors in different order, then  
something in the RGBA path of [Screen](Screen)('MakeTexture') is  
broken, e.g., due to some machine endian issue.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/TextureChannelsTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/TextureChannelsTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/TextureChannelsTest.m</code>
</div>

