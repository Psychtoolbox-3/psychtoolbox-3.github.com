# [PsfToLsf](PsfToLsf)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOptics](PsychOptics)

PSFTOLSF  Convert a line spread function to a point spread function  
    lsf = PSFTOLSF(psf,varargin)  
  
    This works by convolving a horizontal line with a psf and returning the  
    vertical slice through the center.  The spatial support of the lsf is  
    equal to the spatial support of the vertical slice through the passed  
    psf.  The passed psf should be square.  
  
    The returned lsf is normalized to have a peak amplitude of 1.  
  
    See also LSFTOPSF.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOptics/PsfToLsf.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOptics/PsfToLsf.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOptics/PsfToLsf.m</code>
</div>

