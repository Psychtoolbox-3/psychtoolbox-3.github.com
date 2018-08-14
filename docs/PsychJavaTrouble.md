# [PsychJavaTrouble](PsychJavaTrouble)
##### >[Psychtoolbox](Psychtoolbox)>[PsychJava](PsychJava)

[PsychJavaTrouble](PsychJavaTrouble) -- What to do if Java-based Psychtoolbox functions fail?  
  
You probably arrived at this help text because of an error in execution  
of one of the Psychtoolbox Java based functions, e.g., [ListenChar](ListenChar),  
[CharAvail](CharAvail), [GetChar](GetChar) or [FlushEvents](FlushEvents).  
  
These are common reasons for failure of Java based Psychtoolbox  
functions:  
  
1. You run Matlab in nojvm mode, i.e., you started Matlab via 'matlab  
-nojvm'. In that case, Matlabs Java virtual machine is disabled and so  
are all Java based Psychtoolbox functions. In that case you need to  
restart Matlab with its Java VM enabled.  
  
2. You run GNU/Octave, which doesn't support our Java based keyboard  
functions. However, then you should not ever end here, as we use an  
alternate implementation on Octave.  
  
3. The Psychtoolbox/[PsychJava](PsychJava)/ subfolder of your working copy of  
Psychtoolbox isn't included in Matlabs static Java classpath. The  
Psychtoolbox installer/upgrader [(DownloadPsychtoolbox]((DownloadPsychtoolbox), [SetupPsychtoolbox](SetupPsychtoolbox)  
or [UpdatePsychtoolbox](UpdatePsychtoolbox), as well as [DownloadAdditionsForLinux)](DownloadAdditionsForLinux)) usually  
tries to edit the 'classpath.txt' file, or since Matlab 8.1,  
'javaclasspath.txt', of your Matlab installation in order to add the  
Psychtoolbox/[PsychJava](PsychJava) subfolder to Matlabs classpath. This procedure may  
fail due to insufficient access permissions on your system. You can  
verify this by entering 'type classpath.txt' at the Matlab prompt. The  
printed file should contain the path to the [PsychJava](PsychJava) folder. If it  
doesn't, you may want to edit the file yourself ('which classpath.txt'  
tells you the location of the file) or ask a system administrator to do  
it for you. After editing the file you need to restart Matlab. Instead of  
manual editing you can also call this function as [PsychJavaTrouble](PsychJavaTrouble)(1); -  
This will try to automatically modify the classpath.txt or  
javaclasspath.txt file if your Matlab runs with sufficient permissions,  
e.g., administrator permissions.  
  
If you need a quick temporary fix for the problem, other than editing  
classpath.txt and restarting Matlab, then type 'PsychJavaTrouble' at the  
Matlab command prompt. The function will add the [PsychJava](PsychJava) folder to the  
dynamic classpath to immediately enable Java based Psychtoolbox  
functions. This fix is temporary however, it needs to be repeated after  
each restart of Matlab. Executing the command will also clear all  
variables and functions from Matlabs workspace (like 'clear all'), so  
adding it to experiment scripts may impair proper working of that  
scripts.  
  
4. You didn't restart Matlab after the Psychtoolbox installer asked you  
to do so. -\> Restart Matlab and retry.  
  
5. The versions of [GetCharJava](GetCharJava) bundled with Psychtoolbox are incompatible  
with the version of Java installed on your machine or bundled with your  
version of Matlab. If you have a Java SDK installed on your machine,  
Psychtoolbox will try to compile a matching version of [GetCharJava](GetCharJava). This  
should succeed on OS-X but is unlikely to work on Windows, because that  
system does not have a javac compiler installed by default.  
  
6. Other reasons: Post to the Psychtoolbox forum and ask for help.  
  
Good luck!  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychJava/PsychJavaTrouble.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychJava/PsychJavaTrouble.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychJava/PsychJavaTrouble.m</code>
</div>

