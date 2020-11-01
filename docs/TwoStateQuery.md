# [TwoStateQuery](TwoStateQuery)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)>[Utilities](Utilities)

Syntax: [UserResponse](UserResponse) = [TwoStateQuery](TwoStateQuery)[(TheQuestion]((TheQuestion),[[TheChoices](TheChoices)])  
  
Purpose: Create simple dialog box asking user an either/or question.  
On non-GUI setups it will ask a question in the command window instead  
of showing a GUI dialog box.  
  
History:  5/5/04   mpr   decided whether or not to celebrate cinco de mayo  
          10/13/04 mpr   set Yes Button automatically to be enlarged for large  
                         strings   
          1/21/05  mpr   allowed fontsize to shrink for longer questions  
          1/27/05  mpr   allowed question to break at file separator instead of  
                         just spaces   
          6/30/05  mpr   orced underscores to remain as underscores instead of  
                         indicating subscript  
          3/27/06  mpr   changed returned value to -1 when user deletes window;  
                         note that this is dangerous because how a closed  
                         window affects subsequent program behavior is not  
                         implemented the same way in all code calling this  
                         function...   
          5/3/06   mpr   set menubar to none for Version 2006a  
          8/25/06  mpr   resized No Button as needed; could be done better, but    
                         the plan is to keep the 'Yes' and 'No' strings short  
                         so that the code doesn't need to be pushed hard  
          9/29/06  mpr   repainted buttons in version 7  
          1/14/07  mpr   undid previoius fix because button color bug is almost  
                         fixed  
          5/20/13  mk    Add text only fallback for Octave and non-GUI.  
         11/05/15  mk    Add GUI dialog for Octave in GUI mode. White-space cleanup.  
          7/20/17  mk    Use text only fallback on Matlab R2014b and later.  
          7/11/19  dn    GUI version now works on Matlab R2014b and later.  
          8/28/20  mk    Always use questdlg() instead of Matlab specific  
                         figure contraption. Nicer look.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/Utilities/TwoStateQuery.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/Utilities/TwoStateQuery.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/Utilities/TwoStateQuery.m</code>
</div>

