# [PsfToOtf](PsfToOtf)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOptics](PsychOptics)

Convert a 2D point spread function to a 2D optical transfer fucntion.  
   [xSfGridCyclesDeg,ySfGridCyclesDeg,otf] = [PsfToOtf](PsfToOtf)([xGridMinutes,yGridMinutes],psf,varargin)  
  
   Converts a point spread function specified over two-dimensional  
   positions in minutes to a optical transfer function specified over  
   spatial frequency in cycles per degree.  For human vision, these are  
   each natural units.  
  
   The input positions should be specified in matlab's grid matrix format  
   and x and y should be specified over the same spatial extent and with  
   the same number of evenly spaced samples. Position (0,0) should be at  
   location floor(n/2)+1 in each dimension.  The OTF is returned with  
   spatial frequency (0,0) at location floor(n/2)+1 in each dimension.  
  
   Spatial frequencies are returned using the same conventions.  
  
   If you want the spatial frequency representation to have frequency  
   (0,0) in the upper left, as seems to be the more standard Matlab  
   convention, apply ifftshift to the returned value.  That is  
      otfUpperLeft = ifftshift(otf);  
   And then if you want to put it back in the form for passing to our  
   [OtfToPsf](OtfToPsf) routine, apply fftshift:  
      otf = fftshift(otfUpperLeft);  
   The isetbio code (isetbio.org) thinks about [OTFs](OTFs) in the upper left  
   format, at least for its optics structure, which is one place where  
   you'd want to know this convention.  
  
   No normalization is performed.  If the phase of the OTF are very small  
   (less than 1e-10) the routine assumes that the input psf was spatially  
   symmetric around the origin and takes the absolute value of the  
   computed otf so that the returned otf is real.  
  
   We wrote this rather than simply relying on Matlab's potf2psf/psf2otf  
   because we don't understand quite how that shifts position of the  
   passed psf and because we want a routine that deals with the  
   conversion of spatial support to spatial frequency support.  
  
   If you pass the both position args as empty, both sf grids are  
   returned as empty and just the conversion on the OTF is performed.  
  
   [PsychOpticsTest](PsychOpticsTest) shows that this works very well when we go back and  
   forth for diffraction limited OTF/PSF.  But not exactly exactly  
   perfectly.  A signal processing maven might be able to track down  
   whether this is just a numerical thing or whether some is some small  
   error, for example in how position is converted to sf or back again in  
   the [OtfToPsf](OtfToPsf).  
  
   See also [OtfToPsf](OtfToPsf), [PsychOpticsTest](PsychOpticsTest).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOptics/PsfToOtf.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOptics/PsfToOtf.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOptics/PsfToOtf.m</code>
</div>

