# [tcpip](tcpip)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[iViewXToolbox](iViewXToolbox)>[tcp_udp_ip](tcp_udp_ip)>[tcpip](tcpip)

Tcpip toolbox version 1.2.x  2000-12-14 for MATLAB 5.x 6.x  
  
Copyrigtht (C) Peter Rydesaeter 1998 - 2000, Mitthoegskolan, SWEDEN  
  
This program is free software; you can redistribute it and/or  
modify it under the terms of the GNU General Public License  
as published by the Free Software Foundation; either version 2  
of the License, or (at your option) any later version.  
  
This program is distributed in the hope that it will be useful,  
but WITHOUT ANY WARRANTY; without even the implied warranty of  
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the  
GNU General Public License for more details.  
  
You should have received a copy of the GNU General Public License  
along with this program; if not, write to the Free Software  
Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.  
  
Please, send me an e-mail if you use this and/or improve it.  
  
Main implementation:              Implementation of windows support:  
===================  
  
Peter Rydesaeter                  Mario Bergeron  
Mitthoegskolan                    LYR Signal Processing  
Oestersund,Sweden                 Quebec, Canada  
e-mail:Peter.Rydesater@ite.mh.se  e-mail: Mario.Bergeron@lyre.qc.ca  
  
  
Toolbox to do tcpip connection over internet  
and send/receive data from/to matlab.  
  
The core of this toolbox is a mex file.  
Seams to Works well with matlab for Linux (intel),  
Windows 95(98?), Windows NT and  Solaris.  
Should be easy to compile in any unix system.  
  
With this toolbox you can do tcpip connection with  
matlab and transmit data over Intranet/Internet  
Between matlab processes or other applications.  
  
Use tcpip\_open to do a remote connection and get  
a returned handler number that is used for all  
other command.  
tcpip\_servsocket is used to act as a multi-connection  
server.  
All I/O operation is non blocking except tcpip\_servopen  
and tcpip\_write  
  
  
Contents         This help file.  
tcpip\_close      Closes an open tcpip connection.  
tcpip\_open       Opens a new tcpip connection.  
tcpip\_read       Reads an array of bytes from pipe.  
tcpip\_readln     Reads a line of chars (bytes) if their is a complete.  
tcpip\_sendfile   Sends a file throw connection to receiving "tcpip\_getfile"  
tcpip\_getfile    Receives a data from sending "tcpip\_sendfile" and saves to file.  
tcpip\_sendvar    Send matlab variable.  
tcpip\_getvar     Get matlab variable.  
tcpip\_feval      Remote/paralell "feval" executes function remotely in other machine  
tcpip\_feval\_end  Gets remote return arguments from tcpip\_feval  
tcpip\_feval\_server Corresponding server function to tcpip\_feval  
tcpip\_calc\_server  Complete tcpip\_feval\_server includning tcpip\_serveropen....  
tcpip\_servopen   OLD! Only for compatibility. Blocking wait for connetion!  
tcpip\_servsocket Creates a socket binded to a port, waiting for connections!  
tcpip\_listen     Checks/Gets connection connected to tcpip\_servsocket  
tcpip\_status     Returns status of open connection. Detects broken connections.  
tcpip\_viewbuff   Returns whats in receiving buffer but will not empty it.  
tcpip\_write      Sends an array of bytes to connection.  
popmail\_demo     Demo program that read mail from pop mail server.  
webserver\_demo   Matlab as a little webserver, does matlab calculations.  
tcpipmex.c       C-source for the mex file that is core of this toolbox.  
tcpipmex         m-file that will compile the .c-file to mex for your platform.  
tcpipmex.dll     mex file (.dll file) for Windows 95/98, Windows NT  
tcpipmex.mexlx   mex file for Intel Linux matlab 5.x  
tcpipmex.mexglx  mex file for Intel Linux matlab 6.x  
tcpipmex.mexsol  mex file for Sparc Solaris.  
whatsnew.txt     Information about changed between versions  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/tcpip/Contents.m</code>
</div>

{{category}}