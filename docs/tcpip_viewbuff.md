# [tcpip_viewbuff](tcpip_viewbuff)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[iViewXToolbox](iViewXToolbox)>[tcp_udp_ip](tcp_udp_ip)>[tcpip](tcpip)

str=tcpip\_viewbuff(fid,len)  
  
fid   file id for connection.  
len   Maximum length of returned string.  
str   Returned string as char.  
  
  
Returns what's in incomming buffert but it will not  
remove data from the buffert. A following tcpip\_read()  
will return the same string.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_viewbuff.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_viewbuff.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_viewbuff.m</code>
</div>

