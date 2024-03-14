# [SetupPsychtoolbox](SetupPsychtoolbox)
##### >[Psychtoolbox](Psychtoolbox)

[SetupPsychtoolbox](SetupPsychtoolbox) - In-place setup of PTB without network access.  
  
[SetupPsychtoolbox](SetupPsychtoolbox)([tryNonInteractiveSetup=0])  
  
This script prepares an already downloaded working copy of Psychtoolbox  
for use with Matlab or Octave. It sets proper paths and takes care of  
special setup operations for various things.  
  
The optional parameter 'tryNonInteractiveSetup' if provided as 1 (true), will  
try a setup without user interaction, not asking users for input in certain  
situations, but assuming an answer that keeps the setup progressing. Note that  
this is not guaranteed to work in all cases, and may end in data loss, e.g.,  
overwriting an old and potentially user-modified Psychtoolbox installation.  
This non-interactice setup mode is highly experimental, not well tested, not  
supported in case of any trouble!  
  
### Installation is a three step procedure:  
  
1. Download and unpack a full working copy of PTB into your target  
folder. Obviously you need to somehow get a copy, either via conventional  
download from a computer with network connection, visit this URL for that  
download: http://psychtoolbox.org/download.html  
Or from a helpful colleague or copied from some other machine.  
  
2. Change your Matlab/Octave working directory to the Psychtoolbox installation  
folder, e.g., 'cd /Applications/Psychtoolbox'.  
  
3. Type 'SetupPsychtoolbox' to run this script.  
  
  
### If you get stuck, post your question to the forum:  
  
https://psychtoolbox.discourse.group  
  
Please specify your full name and the version of your operating system,  
MATLAB or Octave and Psychtoolbox.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/SetupPsychtoolbox.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/SetupPsychtoolbox.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/SetupPsychtoolbox.m</code>
</div>

