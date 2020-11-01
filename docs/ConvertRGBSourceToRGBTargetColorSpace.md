# [ConvertRGBSourceToRGBTargetColorSpace](ConvertRGBSourceToRGBTargetColorSpace)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[MCSC, outImage] = [ConvertRGBSourceToRGBTargetColorSpace](ConvertRGBSourceToRGBTargetColorSpace)(srcGamut, dstGamut [, image]);  
  
Convert an image from a RGB source colorspace to a RGB target colorspace.  
  
Given two 2-by-4 matrices with the CIE 1931 2D chromaticity coordinates of  
the color primaries red, green, blue and white-point of a source RGB  
colorspace and a destination RGB colorspace, build and return a 3-by-3  
colorspace conversion matrix to convert colors from the source colorspace  
to the target colorspace. Optionally apply the matrix to a RGB or RGBA  
input image, converting it from source to target colorspace.  
  
'srcGamut' must be the 2-by-4 matrix with the primaries and white-point  
of the source color gamut / colorspace.  
  
'dstGamut' can be a 2-by-4 matrix with the primaries and white-point  
of the destination color gamut / colorspace. Alternatively, you can pass  
in the window handle of an open Psychtoolbox onscreen window. In the  
latter case, the function will query that onscreen window for its  
currently assigned colorspace as a convenience. Please note that  
onscreen windows do not have any specific colorspace assigned by  
default, so passing in a window handle to such a window will result in  
this function turning into a no-operation, ie. it will return an identity  
3-by-3 matrix and do nothing to a passed in image. HDR onscreen windows  
as requested via [PsychImaging](PsychImaging)('AddTask', 'General', 'EnableHDR'); will  
have a suitable HDR display colorspace assigned, e.g., the Rec-2020  
colorspace for typical HDR-10 display operation.  
  
'image' is an optional m-by-n-by-3 RGB or m-by-n-by-4 RGBA image matrix.  
If provided, the colorspace conversion will be applied to that image and  
the converted image will be returned as 2nd optional 'outImage' return  
argument.  
  
### Return arguments:  
  
'MCSC' is the 3-by-3 colorspace conversion matrix for going from the  
source colorspace to the target colorspace.  
  
'outImage' is a converted version of the optional 'image' input image. If  
'image' is omitted then 'outImage' is an [] empty matrix.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/ConvertRGBSourceToRGBTargetColorSpace.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/ConvertRGBSourceToRGBTargetColorSpace.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/ConvertRGBSourceToRGBTargetColorSpace.m</code>
</div>

