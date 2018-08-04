# [tcpip_write](tcpip_write)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[iViewXToolbox](iViewXToolbox)>[tcp_udp_ip](tcp_udp_ip)>[tcpip](tcpip)

unsent = tcpip\_write(fid, arg2, arg3, . . .)  
unsent = tcpip\_write(str, arg2 . . .)  
  
fid          is file id number returned from tcpip\_open.  
arg2, arg2   Arrays of any type to send throw  
str          char array must be first argument if fid  
             is not the first. Chould be  str=''  
  
unsent   is returned string with usent charecters.  
         On success an empty char array is returned.  
  
Outputs arrays to tcpip channel. All variables is sent as the  
datatype it is but in network byte order. Notice that a char  
array is sent as one data byte per matlab char.  
If first argument is a scalar double it's used as file id.  
If a char array is given as first argument then last used  
fid (current) is used.  
Usually all character is sent but if their is trouble only  
some or no character is sent, non sent characters is returned.  
  
NOTE: changed from version 1.0 to 1.1 of tcpip toolbox.  
  
### EXAMPLE 1:  
  
 V=23;  
 tcpip\_write(fid,V);  
  
       Sends V as double to tcpip connection in network byte order.  
  
  
### EXAMPLE 2:  
  
 V='Hello World!';  
 tcpip\_write(fid,V);  
  
       Sends text string as array of bytes to tcpip connection;  
  
  
### EXAMPLE 3:  
  
 V=uint16([1 3 0 1024]);  
 tcpip\_write(fid,V);  
  
       Sends 4 uint16 to tcpip connection in network byte order;  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_write.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_write.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_write.m</code>
</div>

