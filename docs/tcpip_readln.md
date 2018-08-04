# [tcpip_readln](tcpip_readln)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[iViewXToolbox](iViewXToolbox)>[tcp_udp_ip](tcp_udp_ip)>[tcpip](tcpip)

[str,ok]=tcpip\_readln(fid,len)  
  
fid   is file id.  
len   is maximum length to be read.  
  
Reads a line of charters terminated by newline character (LF).  
If the a full line (until LF) isn available at the  
moment a empty string will be returned.  
CR and LF characters will not be returned in the string.  
  
Returns ok set to 1 if a complete line whas recived.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_readln.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_readln.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_readln.m</code>
</div>

