# [FitConeFundamentalsTest](FitConeFundamentalsTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[FitConeFundamentalsTest](FitConeFundamentalsTest)  
  
This program allows exploration of how well we can fit  
CIE cone fundamentals with various photopigment nomograms,  
by allowing the lambdaMax to vary.  
  
Note from DHB.  My conclusion after spending some time with  
this is that the best current approach, in the context of the  
CIE fundamentals, is to use the [StockmanSharpe](StockmanSharpe) nomogram and  
its nominal lambdaMax values.  The fit to the 2-degree CIE  
fundamentals is not perfect, but it is pretty good. I think   
the deviations between what is produced by the nominal  
nomogram fit are probaby small compared with our certainty  
about the fundamentals (this is just intuition, but for example  
the deviations are small compared to those between the Stockman-Sharpe  
and Smith-Pokorny fundamentals).  One could try to develope a better  
nomogram, for example by taking the ser/ala polymorphism explicitly  
into account when fitting it, but I'm not sure that would win if one  
wants to keep the convenient assumption of constant photopigment   
absorbance shape along a log wavelength axis.  
  
If one really wanted to go after fitting the fundamentals from parts,  
searching on various densities as well as the lambda max values  
would probably be the way to go.  
  
8/11/11  dhb  Wrote it.  
8/14/11  dhb  Clean up and add comments.  
8/10/13  dhb  A few more notes.  
12/4/20  mk  Add Octave support.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/FitConeFundamentalsTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/FitConeFundamentalsTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/FitConeFundamentalsTest.m</code>
</div>

