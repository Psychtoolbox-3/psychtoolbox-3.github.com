# [ComputeFSSE](ComputeFSSE)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGamma](PsychGamma)

rmse = [ComputeFSSE](ComputeFSSE)(data,predict)  
  
Compute a root fractional SSE between data and prediction.  
Inputs should be column vectors.  
Actual code is:  
  diff = predict-data;  
  rmse = sqrt((diff'\*diff)/(data'\*data));  
  
7/9/14  dhb  Wrote this.  Will replace calls to old and badly named [ComputeRMSE](ComputeRMSE)   
             with calls to this.  This does what [ComputeRMSE](ComputeRMSE) did, but the  
             bad name of [ComputeRMSE](ComputeRMSE) was bugging me too much.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGamma/ComputeFSSE.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGamma/ComputeFSSE.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGamma/ComputeFSSE.m</code>
</div>

