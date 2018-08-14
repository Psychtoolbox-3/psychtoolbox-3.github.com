# [GiveFeedback](GiveFeedback)
##### >[Psychtoolbox](Psychtoolbox)>[Psychometric](Psychometric)

 [GiveFeedback](GiveFeedback)(correct)  
  
 Give auditory feedback about correctness of respose.  One beep for  
 correct, two beeps for incorrect.  Some labs (e.g. dgp) prefer  
 a short beep for correct, no sound for incorrect.  One could  
 easily add a flag to this routine to allow this behavior.  
  
 3/5/97     dhb  Wrote it  
 1/25/00    emw  Added platform conditionals  
 3/8/2000   dgp  Fixed platform conditionals  
 4/14/00   dhb  Fix call to [Snd](Snd) for windows.  
 4/13/02    dgp  Eliminate obsolete calls to [SndPlay](SndPlay). Just call [Snd](Snd) on both platforms.  
                 It's important to specify the sample rate, because the default is  
                 platform-dependent.  
 11/15/03  dhb  Wait for sound to complete before returning.  Failure to do so  
                 was causing problems when [Snd](Snd)('[Close](Close)') was called by calling  
                 routine.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Psychometric/GiveFeedback.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Psychometric/GiveFeedback.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Psychometric/GiveFeedback.m</code>
</div>

