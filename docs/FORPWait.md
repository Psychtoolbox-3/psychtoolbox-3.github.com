# [FORPWait](FORPWait)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[FORP](FORP)

[FORPWait](FORPWait)     Checks for the specified amount of time, if a button of a FORP device  
             (tested for HH-5-CYL) is pressed , returns if a button has been  
             pressed or specified amount of time has passed.  
  
### Usage:      
  
   [[KeyPressed](KeyPressed),[EventTime](EventTime)] = [FORPWait](FORPWait)([Seconds])    
  
### Arguments:  
  
   Seconds             Maximum time to check for buttonpresses in seconds.  
                       Default's to 'wait forever' if not provided.  
  
  
  
Returns the keycode [(KeyPressed)]((KeyPressed)) of the pressed button and the   
time [(EventTime)]((EventTime)) of the status check.  
  
  
   [KeyPressed](KeyPressed)          [KeyCode](KeyCode) of the Pressed Button or empty value if  
                       waiting timed out without any key press.  
  
  
   [EventTime](EventTime)           Time of keypress as returned by [GetSecs](GetSecs).  
  
  
### IMPORTANT NOTE:  
  
   Current-Designs FORP Device (HH-5-CYL) does not return any values for  
   manufacturer or product, so i used the [VendorID](VendorID) returned by   
   [PsychHID](PsychHID)('Devices') for the HH-5-CYL.(ATM i do no really know if the   
   [VendorID](VendorID) has unique values).  
   Another issue i had to solve was a ?bug? using 'GetReport'. I had to   
   close the Callbackhandlers to the current device by calling   
   'ReceiveReportsStop' before calling 'GetReport' on another device.  
   If you have got any advice for a better way solve those problems, feel   
   free to let me know:  
  
          Florian Stendel   
          Visual Processing Lab  
          Universitaets - Augenklinik Magdeburg  
          Leipziger Strasse 44  
          39120 Magdeburg  
          Tel:    0049 (0)391 67 21723  
          Email:  vincentdhs@gmx.de  
  
  
   09/10/06   fs   Wrote it.  
   19/10/06   fs   Added some further improvements suggested by Mario  
                   Kleiner.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/FORP/FORPWait.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/FORP/FORPWait.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/FORP/FORPWait.m</code>
</div>

