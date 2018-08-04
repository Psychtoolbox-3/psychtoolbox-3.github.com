# [GetNTP](GetNTP)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[GetNTP](GetNTP) - Query time from NTP server  
  
socket = [GetNTP](GetNTP)( 'open', 'hostname' )  
pkg = [GetNTP](GetNTP)( 'read', socket[, dbg ] )  
[GetNTP](GetNTP)( 'close', socket )  
  
[GetNTP](GetNTP) is a very simple pnet based NTP client to query time from an NTP  
server over the network.  
  
A pnet socket has to be created with the open command first. The read  
command returns a structure with the fields timestamps, delay and rtt.  
pkg.timestamps is a vector of four timestamps reflecting client send  
time, server receive time, server transmit time, and client receive time.  
pkg.delay is the network delay as specified by the NTP specification.  
pkg.rtt is the round-trip-time.  
  
If dbg is true the NTP header is decoded completely and added to the  
returned structure including the NTP server's reference timestamp for  
debugging. Additionally server receive and transmit timestamps are  
printed to the console in human readable format.  
  
Note that any argument checking and error handling was omitted  
intentionally to improve timing with [NetStation](NetStation) synchronization.  
  
Reference: Mills, D. L. (2006). Network Time Protocol Version 4  
Reference and Implementation Guide. Retrieved May 21, 2017 from  
https://www.eecis.udel.edu/~mills/database/reports/ntp4/ntp4.pdf  
  
Author: Andreas Widmann, University of Leipzig, 2017  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/GetNTP.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/GetNTP.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/GetNTP.m</code>
</div>

