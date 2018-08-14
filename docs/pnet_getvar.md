# [pnet_getvar](pnet_getvar)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[iViewXToolbox](iViewXToolbox)>[tcp_udp_ip](tcp_udp_ip)

PNET\_GETVAR - Gets any matlab variable (number-, cell-, struct- or object -array) from pnet.  
  
### Syntax:    
  
  [variable1, variable2,.....]=pnet\_getvar(con)  
  
  Receives matlab variables over a TCP connection that was sent with  
  PNET\_PUTVAR. This variable transfer uses its own non standard protocol.  
  Can also be used with UDP packets if the variable/variables fits inside  
  an UDP packet.  
  
Se also:  PNET\_PUTVAR, PNET, PNET\_REMOTE  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/pnet_getvar.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/pnet_getvar.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/pnet_getvar.m</code>
</div>

