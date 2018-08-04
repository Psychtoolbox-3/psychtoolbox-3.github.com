# [MultiNormalDraw](MultiNormalDraw)
##### >[Psychtoolbox](Psychtoolbox)>[PsychProbability](PsychProbability)

x = [MultiNormalDraw](MultiNormalDraw)(n,u,K)  
  
Make n multivariate normal draws with mean u and covariance matrix K.  
Each draw is in a single column of y, which has n columns.  
  
The routine operates by computing the appropriate linear transformation  
of a N(0,I) multivariate normal draw.  This transformation is given by   
y= C'x + u where K = C'C.  This works because the covariance of a  
distribution y = Cx is in general given by Ky = C Kx C'.  In our case   
Kx= I so Ky = C'C = K.  
  
K = 0 is handled as a special case  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychProbability/MultiNormalDraw.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychProbability/MultiNormalDraw.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychProbability/MultiNormalDraw.m</code>
</div>

