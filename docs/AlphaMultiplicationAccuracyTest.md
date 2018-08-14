# [AlphaMultiplicationAccuracyTest](AlphaMultiplicationAccuracyTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[maximumError, roundTypeStr, independentFlag]=[AlphaMultiplicationAccuracyTest](AlphaMultiplicationAccuracyTest)([screenNumber])  
  
Test the accuracy of alpha blending multiplication. [OpenGL](OpenGL) guarantees  
perfect accuracy of alpha multiplication for values 0 and 1 only.  
[AlphaMultiplicationAccuracyTest](AlphaMultiplicationAccuracyTest) measures accuracy of intermediate values.  
  
Return argument "maximumError" is the maximum unsigned difference between  
[OpenGL](OpenGL) alpha multiplication and  simulated alpha blending in MATLAB using  
double-precisions floating point multiplication.  
  
### Values of maximumError fall into three categories:  
  
0 <= maximumError < 0.5   : [OpenGL](OpenGL) rounds to nearest integer.  No   
                            accuracy loss for a single multiplication.  
  
0.5 <= maximumError < 1   : [OpenGL](OpenGL) truncates or rounds up. For a single   
                            multiplication, Accuracy is off  0.5 parts  
                            in 255 more than would multiplying luminances   
                            using floating-point values and rounding.  
  
maximumError \>= 1         : Something is wrong.    
  
  
[AlphaMultiplicationAccuracyTest](AlphaMultiplicationAccuracyTest) tries to determine whether [OpenGL](OpenGL) alpha  
multiplication rounds to the nearest integer, rounds down or rounds up  
and returns in "roundTypeStr" a string indicating which, either, "round"  
"floor", or "ceil".  If [AlphaMultiplicationAccuracyTest](AlphaMultiplicationAccuracyTest) can not determine  
the rounding method, then it returns "unknown".  
  
[AlphaMultiplicationAccuracyTest](AlphaMultiplicationAccuracyTest) also tests that multiplication errors are  
independent of the choice of blending factor string and the blending  
surface, setting return argument "independentFlag" accordingly.       
  
Because in [OpenGL](OpenGL) pixel color components are ultimately encoded as 8-bit  
integers in video RAM, the results of [OpenGL](OpenGL) alpha multiplicaion will be  
less accurate than those predicted by floating-point calculations.  If  
[OpenGL](OpenGL) rounds to the nearest integer then the alpha multiply error will  
be less than 0.5. This is the limit of precision of the color components  
of a pixel. Therefore, when alpha blending rounds to the nearest integer,  
no more accuracy is lost with [OpenGL](OpenGL) alpha blending than by calculating  
pixel values in MATLAB with floating point precision then rounding them  
to integer pixel values for display.  
  
Note that errors are cumulative and iterative alpha multiplication, in  
which a product of a prevoius multiplication becomes a factor in a  
subsequent multiplication, can produce large errors, even in the best  
case of rounding where 0 <= maximumError < 0.5.  Note also that A single  
alpha blending operation may result in two multipliations, because both  
source and destination surfaces may be multiplied before they are added.   
  
We test blending accuracy becasue [OpenGL](OpenGL) makes no gurantees.  The [OpenGL](OpenGL)  
policy on alpha multiplician is summarized here:    
  
http://msdn.microsoft.com/library/default.asp?url=/library/en-us/opengl/glfunc01\_4vs3.asp  
  
        "Despite the apparent precision of the above equations, blending  
        arithmetic is not exactly specified, because blending operates with  
        imprecise integer color values. However, a blend factor that should be  
        equal to one is guaranteed not to modify its multiplicand, and a blend  
        factor equal to zero reduces its multiplicand to zero."   
  
See also: [AlphaBlendingTest](AlphaBlendingTest), [PsychAlphaBlending](PsychAlphaBlending)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/AlphaMultiplicationAccuracyTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/AlphaMultiplicationAccuracyTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/AlphaMultiplicationAccuracyTest.m</code>
</div>

