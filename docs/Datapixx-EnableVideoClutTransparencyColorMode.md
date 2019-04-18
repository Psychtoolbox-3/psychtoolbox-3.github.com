# [Datapixx('EnableVideoClutTransparencyColorMode')](Datapixx-EnableVideoClutTransparencyColorMode) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('EnableVideoClutTransparencyColorMode');

M16 video mode supports an overlay whose colors are loaded via [SetVideoClut](SetVideoClut).  
This function allows one CLUT color to indicate transparency, permitting the  
underlying M16 pixel to show through.  
This feature could be used in dual-display environments where overlay  
information might be shown on the console,  
whereas the main testing display would show only the underlying stimulus.  
See [DatapixxM16Demo](DatapixxM16Demo) for an example.  
  


###See also:
[DisableVideoClutTransparencyColorMode](Datapixx-DisableVideoClutTransparencyColorMode), [SetVideoMode](Datapixx-SetVideoMode), [SetVideoClut](Datapixx-SetVideoClut), [SetVideoClutTransparencyColor](Datapixx-SetVideoClutTransparencyColor)
