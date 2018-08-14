# [tcpip_status](tcpip_status)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[iViewXToolbox](iViewXToolbox)>[tcp_udp_ip](tcp_udp_ip)>[tcpip](tcpip)

status=tcpip\_status(fid) Return a status value for tcpip connection.  
  
Mainly usefull when you whant to detect that a connection is broken.  
(return value 0)  
  
### Possible status values:  
  
TCPIP\_NOCONNECT   0 Not connected. Perhaps it has been broken. [Close](Close) it!  
TCPIP\_SERVSOCKET  1   Server socket waiting for connections.  
TCPIP\_STDIO       5   Connected to file (not implemented)  
TCPIP\_CLIENT      10  Connected as client. Used tcpip\_open.  
TCPIP\_SERVER      12  Connected as server  Used tcpip\_servopen or tcpip\_listen  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_status.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_status.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_status.m</code>
</div>

