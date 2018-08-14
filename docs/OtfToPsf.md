# [OtfToPsf](OtfToPsf)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOptics](PsychOptics)

OTFTOPSF  Convert a 2D optical transfer fucntion to a 2D point spread function.  
    [xSfGridCyclesDeg,ySfGridCyclesDeg,otf] = [PsfToOtf](PsfToOtf)([xGridMinutes,yGridMinutes],psf)  
  
    Converts a optical transfer function specified over two-dimensional  
    spatial frequency in cycles per degree to a point spread function  
    specified over positions in minutes.  For human vision, these are each  
    natural units.  
  
    The input spatial frequencies should be specified in matlab's grid  
    matrix format and sf for x and y should be specified over the same  
    spatialfrequency extent and with the same number of evenly spaced  
    samples. Spatial frequency (0,0) should be at location floor(n/2)+1 in  
    each dimension.  The PSF is returned with position (0,0) at location  
    floor(n/2)+1 in each dimension.  This is the form we mostly want to  
    look at and use.    
  
    The OTF is assummed to have the DC term in the center poistion,  
    floor(n/2)+1 of the passed matrix.  If you have your hands on an OTF  
    with the DC term in the upper left position (1,1), apply fftshift to  
    it before passing to this routine.  The DC in upper left is the Matlab  
    native format for applying the ifft, and is also the format stored by  
    isetbio in its optics structure.  
  
    Positions are returned using the same conventions.  
  
    No normalization is performed.  The psf should be real, and we  
    complain (throw an error) if it is not, to reasonable numerial  
    precision. If it seems OK, we make sure it is real.  
  
    We also make sure that the returned psf is all postive and sums to   
    1.  In some cases, we found that there were small negative values  
    and after setting these to zero renormalization was needed.  
  
    We wrote this rather than simply relying on Matlab otf2psf/psf2otf  
    because we want a routine that deals with the conversion of spatial  
    frequency to spatial support.  
  
    If you pass the both sf args as empty, both position grids are  
    returned as empty and just the conversion on the OTF is performed.  
  
    [PsychOpticsTest](PsychOpticsTest) shows that this works very well when we go back and  
    forth for diffraction limited OTF/PSF.  But not exactly exactly  
    perfectly.  A signal processing maven might be able to track down  
    whether this is just a numerical thing or whether some is some small  
    error, for example in how position is converted to sf or back again in  
    the [PsfToOtf](PsfToOtf).  
  
 Optional key/value pairs:  
    'warningInsteadOfErrorForNegativeValuedPSF'  - Set to 1 (default  
                                                   0) to get a warning  
                                                   not an error if the psf  
                                                   values are too negative  
                                                   before they are forced  
                                                   to zero. Set to 2 for  
                                                   no warning msg or  
                                                   error.  
    'negativeFractionalTolerance'                - The error/warning is  
                                                   thrown if the magnitude  
                                                   of the most negative  
                                                   value is more than this  
                                                   fraction of the maximum  
                                                   (positve) value.  
                                                   (Default 1e-3).  
  
 See also: [PsfToOtf](PsfToOtf), [PsychOpticsTest](PsychOpticsTest).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOptics/OtfToPsf.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOptics/OtfToPsf.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOptics/OtfToPsf.m</code>
</div>

