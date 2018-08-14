# [FitCumGauss_MES](FitCumGauss_MES)
##### >[Psychtoolbox](Psychtoolbox)>[PsychStairCase](PsychStairCase)

Fits a cumulative Gaussian to a set of probe values and subject responses  
  
[loglik,m,d] = [FitCumGauss](FitCumGauss)\_MES(p,r,mset,dset,lapserate,guessrate)  
Computes likelihood of each combination of [PSEs](PSEs) mset and slopes dset  
given a set of probe values and responses using a cumulative Gaussian.  
  
For ease of thinking about it you can view responses as either 0 or 1,  
though in practice anything larger than 0 is treated as 1 and anything  
lower than 0, including 0, is treated as 0. A 1, -1 response scheme as  
input is thus no problem.  
  
By default, a psychometric function ranging from 0% to 100% is used, as  
is suitable for discrimination experiments with a standard in the middle  
of the possible stimulus parameter range. For other paradigms, such as  
detection tasks, one can set the guessrate input to 1/num\_alternatives,  
e.g. .5 when doing a 2IFC detection task.  
  
Optinally fits with a lapse rate, which defaults to 0. If a lapse rate is  
set, the cumulative Gaussian levels off at lapserate/2 and 1-lapserate/2  
when the guessrate is 0. If the guessrate is non zero, the cumulative  
Gaussian that is fit ranges from guessrate to 1-lapserate  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychStairCase/FitCumGauss_MES.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychStairCase/FitCumGauss_MES.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychStairCase/FitCumGauss_MES.m</code>
</div>

