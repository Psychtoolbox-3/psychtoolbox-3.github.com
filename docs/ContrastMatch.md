# [ContrastMatch](ContrastMatch)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

 weight=[ContrastMatch](ContrastMatch)(device,dimWeight,[foreColor],[backColor])  
  
 Displays two gratings. The bright grating alternates white and weight\*white,  
 producing luminances [LMax](LMax) and [LBright](LBright).  
 The dim grating alternates dimWeight\*white and black, producing luminances  
 [LDim](LDim) and [LMin](LMin).  
 When the grating contrasts match, [LMax](LMax)/[LBright](LBright)=[LDim](LDim)/[LMin](LMin).  
 In a more compact notation, L1/Lb=Ld/L0. We set the weight wd that produces  
 Ld, and the observer adjusts the weight wb that produces Lb. They are related  
 by the gamma function, y=g(w), where y is the normalized luminance,  
 y=(L-L0)/(L1-L0). We know wb and wd, and we have access to the gamma function,  
 so we can compute yb and yd. Solving for L, we have  
    L=y\*(L1-L0)+L0  
 Our relation at match can be rewritten as  
    L1\*L0=Ld\*Lb  
    0=Ld\*Lb-L1\*L0  
    =(yd\*(L1-L0)+L0)\*(yb\*(L1-L0)+L0)-L1\*L0  
    Let's divide by L1^2, and define r=L0/L1.  
    =(yd\*(1-r)+r)\*(yb\*(1-r)+r)-r  
    This is a quadratic equation in r  
    =(yd+(1-yd)\*r)\*(yb+(1-yb)\*r)-r  
    =yd\*yb+(yb\*(1-yd)+yd\*(1-yb)-1)\*r+(1-yd)\*(1-yb)\*r^2  
    c=[(1-yd)\*(1-yb) yb\*(1-yd)+yd\*(1-yb)-1 yd\*yb]; % coefficients of quadratic polynomial  
    r=roots(c)  
 The answer, r, is the desired ratio of L0/L1.  
  
 5/28/96 dgp  Wrote it.  
 5/28/96 dgp  Updated to use new [GetMouse](GetMouse), that flushes mouse events.  
 8/4/96  dhb  Changed name to [ContrastMatch](ContrastMatch).  
 8/16/97 dgp  Changed "text" to "theText" to avoid conflict with TEXT function.  
 7/19/98 dgp  Removed obsolete TIMER.  
 6/30/03 dgp Updated [Screen](Screen) [OpenScreen](OpenScreen) to [Screen](Screen) [OpenWindow](OpenWindow).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/ContrastMatch.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/ContrastMatch.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/ContrastMatch.m</code>
</div>

