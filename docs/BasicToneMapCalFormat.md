# [BasicToneMapCalFormat](BasicToneMapCalFormat)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

outputXYZCalFormat = [BasicToneMapCalFormat](BasicToneMapCalFormat)(inputXYZCalFormat, maxLum)  
  
Simple tone mapping.  Leaves any pixel with luminance below maxLum alone.  
For pixels whose luminance exceeds maxLum, scale XYZ down multiplicatively so  
that luminance is maxLum.  
  
10/1/09 bjh, dhb     Created it.  
10/4/09 dhb          Debug and make it work right.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/BasicToneMapCalFormat.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/BasicToneMapCalFormat.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/BasicToneMapCalFormat.m</code>
</div>

