# [psychsendmail](psychsendmail)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[iViewXToolbox](iViewXToolbox)>[cbase64](cbase64)

SENDMAIL Send Internet e-mail  
  Using SENDMAIL (which needs the TCP/UDP/IP toolbox, freely available from  
  http://petrydpc.ite.mh.se/tools/) it is possible to send e-mail messages  
  from the Matlab prompt. This can be useful when you want to be notified  
  when large jobs terminate on remote machines.  
  
Usage  
  [RETCODE] = SENDMAIL(FROM, TO, SUBJ, MESG [, FILENAME]) send an e-mail with  
  subject SUBJ and contents MESG to the email address in TO, with  
  the From: field set to FROM.  
  
  FROM, TO and SUBJ are Matlab strings. MESG can be either a  
  string, or a cell array of strings.  
  
  RETCODE is 0 if the message was sent succesfully, otherwise it  
  has the value -1.  
  
  The optional argument FILENAME is a string containing the  
  filename of the file to be attached to the message. It may  
  contain path information.  
  
Examples  
  sendmail('me@some.where.com','me@else.where.org','Job Finished!','It took 4 days, 12 hours,6 minutes.')  
  
  sendmail('me@some.where.com','me@else.where.org','Job Finished!','Finaly...', 'results.mat')  
  
Installation  
  1. Make sure the TCP/UDP/IP toolbox is somewhere in your PATH  
  2. Adjust the SMTPSERVER, SMTPSERVERPORT and CLIENTIP variables to reflect your situation.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/iViewXToolbox/cbase64/psychsendmail.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/iViewXToolbox/cbase64/psychsendmail.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/iViewXToolbox/cbase64/psychsendmail.m</code>
</div>

