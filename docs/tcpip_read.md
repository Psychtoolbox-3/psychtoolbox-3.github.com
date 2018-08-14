# [tcpip_read](tcpip_read)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[iViewXToolbox](iViewXToolbox)>[tcp_udp_ip](tcp_udp_ip)>[tcpip](tcpip)

str=tcpip\_read(fid,len,datatype)  
str=tcpip\_read(fid,len)  
  
fid       is file id.  
len       is maximum length to be read.  
datatype  optional char array argument specifying what datatype to read.  
  
Read given number of characters (bytes) OR elements of other datatype  
if specified. Data vill be returned as specified datatype.  
Se  fwrite   for more about names of different datatypes.  
  
Operation will be interupted before len is reached if their  
is no more character to read at the moment. (non blocking)  
  
  
### Problems:  
  
Type conversion from the tcpipstream of 'char' is stream is slow!!!!  
If you use this functionality you schuold know their is better  
ways of doing it! u8read()   and u8write() are available at mathworks    
user contributed ftp site and are probably better way of convert  
this stream of char to other data types afterwords in your script.  
  
Somethink similar will be included in future inside the toolbox....  
  
  
### EXAMPLE 1:  
  
   data=tcpip\_read(fid,20,'double');  
  
         Reads (max) 20 elements of type 'double' from tcpip connection.  
  
  
### EXAMPLE 2:  
  
   data=tcpip\_read(fid,20);  
  
            Reads characters (bytes) from tcpip connection.  
  
  
### EXAMPLE 3:  
  
   data=tcpip\_read(fid,1024,'uint16');  
  
            Reads 1024 elements of datatype uint16.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_read.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_read.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/tcpip_read.m</code>
</div>

