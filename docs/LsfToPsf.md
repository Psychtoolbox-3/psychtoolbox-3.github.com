# [LsfToPsf](LsfToPsf)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOptics](PsychOptics)

[LSFToPSF](LSFToPSF)  Convert a line spread function to a point spread function.  
   psf = LSFTOPSF(lsf,varargin)  
  
   This works by taking the lsf into the one-dimensional frequency domain  
   (i.e. get the 1D MTF) and then creating a circularly symmetric version  
   of this.  The 2D frequency representation is then converted back to the  
   spatial domain to produce the psf.  This produces a spatially-symmetric  
   PSF consistent with the measured line spread function.  
  
   This method is described by Marchand, 1964, JOSA, 54, 7, pp. 915-919  
   and is one of several methods provided.  In 1964, taking the Fourier  
   transform was computationally intense.   
  
   There is a second paper by Marchand (1965, JOSA, 55, 4, 352-354) which  
   treats the more general case where you have line spread functions for  
   many orientations and want to recover an psf that is not necessarily  
   spatially-symmetric.  
  
   The lsf must be spatially symmetric.  This makes sense given that we  
   are going to recover a spatially symmetric psf.  
  
   You want to make sure that the spatial suport is large enough to  
   capture the full lsf.  
  
   The returned psf is normalized to have unit volume.  
  
   See also PSFTOLSF, PSYCHOPTICSTEST  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOptics/LsfToPsf.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOptics/LsfToPsf.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOptics/LsfToPsf.m</code>
</div>

