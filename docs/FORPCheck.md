# [FORPCheck](FORPCheck)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[FORP](FORP)

[FORPCheck](FORPCheck) Checks if a button of a FORP device (HH-5-CYL) is pressed.  
  
### Usage:      
  
   [[KeyPressed](KeyPressed),[EventTime](EventTime)] = [FORPCheck](FORPCheck)()    
  
  
Return the key name [(KeyPressed)]((KeyPressed)) of the pressed button and the   
time [(EventTime)]((EventTime)) of the status check.  
  
  
   [KeyPressed](KeyPressed)          Key name of the Pressed Button, empty string  
                       if none pressed.  
  
  
   [EventTime](EventTime)           Time of keypress check, as returned by [GetSecs](GetSecs).  
  
### IMPORTANT NOTE:  
  
  
   See [FORPWait](FORPWait).  
  
   Going through each device can be very time consuming. If would advise  
   to unplug each unnecessary device, so less devices has to be checked.  
   If you have got any advice for a better way to solve those problems, feel   
   free to let me know:  
  
          Florian Stendel   
          Visual Processing Lab  
          Universitaets - Augenklinik Magdeburg  
          Leipziger Strasse 44  
          39120 Magdeburg  
          Tel:    0049 (0)391 67 21723  
          Email:  vincentdhs@gmx.de  
  
  
   10/10/06   fs   Wrote it.  
   10/16/06   mk   Add caching of device index.  
   10/17/06   fs   Done some restructuring and testing.   
   02/08/07   mk   New vendor id 6171 added to valid device lists.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/FORP/FORPCheck.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/FORP/FORPCheck.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/FORP/FORPCheck.m</code>
</div>

