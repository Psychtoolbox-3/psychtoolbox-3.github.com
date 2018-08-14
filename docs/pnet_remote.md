# [pnet_remote](pnet_remote)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[iViewXToolbox](iViewXToolbox)>[tcp_udp_ip](tcp_udp_ip)

PNET\_REMOTE   - Evaluation of matlab expression in remote host PNET  
  
    Version: First includes in the tcp/udp/ip toolbox 2002-02-13  
             (C) 2002 Peter Rydesaeter, GNU Public License   
  
    This function uses PNET for nonblocking remote controll of other matlab   
    session on this or other hosts. This function implements different client  
    and server calls in same function. By setting the server matlab session  
    in server mode with "PNET\_REMOTE SERVER ..." its possible to connect to  
    it from other hosts and matlab sessions with "PNET\_REMOTE con EVAL ..."  
    or exchange data with PUT or GET options. This remote controll package  
    uses its own (non standard) protocol over a TCP/IP connection.  
  
    Optional parameters are enclosed in [ ] in follwing syntax description.  
  
###  SYNTAX:  
 =======    
  
 pnet\_remote('server',[ port ])  
  
    Starts to listen on specified port (is by default 5678) for a connection  
    and starts to serv for EVAL, PUT, GET... commands sent from remotehost.  
    It listens for a connection, servers it until it closes and then starts  
    to listens for a new connection to serv.  
  
 pnet\_remote(con,'serverat')  
  
    Like the last but it starts to serv on an already estabished connection  
    until it is closed by the remote host. CON needs to be closed afterwards.  
  
 con=pnet\_remote('connect',['host',[ port ] ])  
  
    Connects and returns a connection handler to a "PNET\_REMOTE SERVER"  
    at specified HOST and PORT. Default value for host is 'localhost' and  
    for port 5678. A connection an also be established with  
    PNET('TCPCONNECT',...).   
  
 pnet\_remote(con,'close')  
  
    Sends a close command to remote host and closes the connection.  
    PNET(con,'CLOSE')  should also work even if it is not sending the close  
    command.  
  
 pnet\_remote(con,'close')  
  
    Exactly the same as PNET('CLOSEALL')  
  
 pnet\_remote(con,'eval','expression')  
  
    Non blocking evaluation of expression on remote host. The expression is  
    evaluated in callers namespace. The expression is a regular matlab  
    expression evaualted with EVALIN. This command is NONBLOCKING and  
    status of the evaluation can be detected with PNET\_REMOTE(con,'STATUS')  
  
 stat=pnet\_remote(con,'status')  
  
    Returns evaluation status of a remote host/session. The returned value  
    is a string containing 'busy' 'error'  or 'ready'  depending on status  
    of evaluation. during evaluation 'busy' is returned, then 'error' or  
    'ready' is returened depending on if EVALIN succeded.  
  
 pnet\_remote(con,'PUT','name1',expr1, 'name2',expr2.....)  
  
    Uploads variables to remote hosts evaulation workspace. Its specified  
    as a list of pairs of 'NAME' and EXPR where 'NAME' is the new name  
    of the uploaded variable in the remote workspace and EXPR is a local  
    variabel or expression.  
  
 [var1,var2,...]=pnet\_remote(con,'GET','name1','name2'....)  
  
    Gets specified variables from remote workspace. Actually can 'name..'  
    be any expression that is remote evaluated \_but\_ this command blocks  
    until the result of the remotely evaluted expression/variable is    
    recived.  
  
 pnet\_remote(con,'PUTSCRIPT','scriptname1','scriptname2',....)  
  
    Uploads local scripts to the remote host. The scripts are put on the   
    remote hosts search path in a directory named PNET\_PUTSCRIPTS.  
    'scriptname...' is the name used at calls. WHICH is used to detect  
    full path and extention of the script. If the remote hosts platform/OS is  
    different then the full extention on MEX files must be specified.  
  
 pnet\_remote(con,'BREAK')  
  
    Sends a break comand to the script running on the remote host. This break  
    comand can only be detected if the remote host repeatedly calls  
    PNET\_REMOTE('GET\_BREAK')  which will cause an error in the remote script.  
  
 pnet\_remote('GET\_BREAK')    
  
    Used to be repeatedly called in scripts on the remote host. On a recived  
    BREAK or disconected connection an error will be generated that break  
    the running script.  
  
###  General alternative syntax(es):  
  
      pnet\_remote server port  
  
    This is the same as the functional form PNET\_REMOTE('SERVER',port)   
    Numbers like connection handlers and port-numbers can be specified  
    as strings in most cases. This syntax should generaly work for all  
     variants of calls.  
  
      con\_array=[con1 con2 con3 .....]  
      pnet\_remote(con\_array,.........)  
  
    You can specify the conection handler as an array of connections and  
    same operation will be performed for all connections.  
    This syntax should generaly work for all variants of calls \_IF\_ they    
    do not return anything.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/pnet_remote.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/pnet_remote.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/iViewXToolbox/tcp_udp_ip/pnet_remote.m</code>
</div>

