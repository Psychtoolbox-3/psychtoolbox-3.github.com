# [ComputeRMSE](ComputeRMSE)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGamma](PsychGamma)

rmse = [ComputeRMSE](ComputeRMSE)(data,predict,SUPRESS\_WARNING)  
  
Compute a root fractional SSE between data and prediction.  
Inputs should be column vectors.  
  
The routine badly named, because what it computes  
is not what anyone would call an RMSE.  A better  
name for the routine would be [ComptueFSSE](ComptueFSSE) or something  
like that.  
  
Indeed, it now calls through an appropriately named  
[ComputeFSSE](ComputeFSSE), and issues an annoying warning encouraging  
the user to change the calling form.  
  
2/3/96   dhb  Added improved comments.  
1/13/13  dhb  Added cautionary comment about what this routine does.  
              as well as message that would tell an unsuspecting user  
              at runtime.  
         dhb  Added mechanism to suppress the warning message.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGamma/ComputeRMSE.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGamma/ComputeRMSE.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGamma/ComputeRMSE.m</code>
</div>

