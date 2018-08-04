# [udp_send_demo](udp_send_demo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[iViewXToolbox](iViewXToolbox)>[tcp_udp_ip](tcp_udp_ip)

UDP\_SEND\_DEMO - a demo that sends a squence of doubles in network byte order to local or remote host  
  
Syntax:  
  UDP\_SEND\_DEMO  
or  
  UDP\_SEND\_DEMO function\_string  
or  
  UDP\_SEND\_DEMO function\_string hostname  
or  
  UDP\_SEND\_DEMO function\_string hostname portnumber  
  
Default values:  
   function\_string  is by default sin(0:0.1:6) that will be evaluated and transmitted   
                    as a sequence of network byte ordered doubles (or generated datatype)  
  
   hostname         is by default localhost but can be any hostname if you whant to send  
                    the packet to an other host.  
  
   portnumber       is by default 3333.  
  
  
The purpose of this demo is to illustrate how a udp packat can be created, filled with numbers  
and then transmitted to any host and udp port. Use this demo together with udp\_plotter\_demo  
that receives and plott the packets of numbers.  
  
### Example:  
  
udp\_send\_demo sin(0:0.1:50)./(0:0.1:50) plotterhost 33333  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/udp_send_demo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/udp_send_demo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/udp_send_demo.m</code>
</div>

