# [CreateUniformDotsIn3DFrustum](CreateUniformDotsIn3DFrustum)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[x,y,z] = [CreateUniformDotsIn3DFrustum](CreateUniformDotsIn3DFrustum)(ndots,FOV,aspectr,depthrangen,depthrangef,eyeheight)  
  
[Sample](Sample) dots in frustum uniformly, creating a cloud tightly fitting in the  
frustum. When the optional 6th parameter eyeheight is given, dots will be  
uniformly sampled on a ground plane at -eyeheight.  
  
z is not sampled from a uniform distribution, but from a parabolic  
distribution as the area of cross sections of the frustum is a quadratic  
function of the depth plane's depth ( (z\*2\*tan(FOV/2))^2 \* aspectr )  
  
Here, I use Inverse transform sampling to transform a uniform random  
variable into the quadratic shape random variable  
see Luc Devroye. Non-Uniform Random Variate Generation. New York:  
Springer-Verlag, 1986. Chapter 2  
(http://cg.scs.carleton.ca/~luc/chapter\_two.pdf)  
# compile following in latex to see full derivation  
\documentclass[12pt,a4paper]{minimal}  
\usepackage{amsmath}        % math  
  
\begin{document}  
\textbf{Derivation}:\\  
Use pdf related to cross-section surface of frustum:  
\(\left(2 z \tan\left(\frac{FOV}{2}\right)\right)^2 aspectr\)\\  
\(z\_1\) is the distance of the near depth plane\\  
\(z\_2\) is the distance of the far depth plane\\  
\(y\) is a uniform random variable\\  
Given: \(F(z\_2)=1\) and \(F(z\_1)=0\).  
\begin{align}  
    F(z) &= \int\limits^z\_{z\_1} k z^2 \, \mathrm{d}z\\  
    F(z) &= \frac{k}{3} \left(z^3 - z\_1^3\right)\\  
    k    &= \frac{3}{z\_2^3-z\_1^3}\\  
    F(z) &= \frac{z^3-z\_1^3}{z\_2^3-z\_1^3}  
\end{align}  
Substitute \(y\) for \(F(z)\) and factor out \(z\):  
\begin{align}  
    z^3  &= y\left(z\_2^3-z\_1^3\right) + z\_1^3\\  
    z    &= \sqrt[3]{y\left(z\_2^3-z\_1^3\right) + z\_1^3}  
\end{align}\\  
For a ground plane, the width of the frustum at depth \(z\) is given by  
\(2 z \tan\left(\frac{FOV}{2}\right) aspectr\).\\  
By following the same inverse transform sampling steps, we would end up  
with   
\[ z = \sqrt{y\left(z\_2^2-z\_1^2\right) + z\_1^2} \]  
for the linear distribution between \(z\_1\) and \(z\_2\).  
  
\end{document}  
----  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/CreateUniformDotsIn3DFrustum.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/CreateUniformDotsIn3DFrustum.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/CreateUniformDotsIn3DFrustum.m</code>
</div>

