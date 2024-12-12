# [PsychLicenseHandling](PsychLicenseHandling)
##### >[Psychtoolbox](Psychtoolbox)

[PsychLicenseHandling](PsychLicenseHandling) - Manage Psychtoolbox software licensing.  
  
This function facilitates the setup and administration of license  
management for Psychtoolbox on operating systems and platforms that  
require either a paid license or a time-limited free trial.  
  
Once license management is configured for your operating system and  
hardware, you can manage your license, including activation and  
deactivation on a machine, checking licensing status, and generating a  
support authentication token.  
  
### For information on purchasing license keys for Psychtoolbox, visit:  
  
https://www.psychtoolbox.net  
  
The prebuilt, tested, and supported mex files included in Psychtoolbox  
are provided by our commercial host company, Medical Innovations  
Incubator [GmbH](GmbH), as of November 2024. Contact details are as follows:  
  
Medical Innovations Incubator [GmbH](GmbH)  
Eisenbahnstr. 63  
72070 Tübingen  
Germany  
  
Commercial register: HRB 751684  
Register court: Local court Stuttgart, Germany  
  
For general and data protection inquiries, email: info@mi-incubator.com  
For Psychtoolbox questions, email: psychtoolbox@mi-incubator.com  
  
The data protection and privacy statements related to Psychtoolbox  
software license management and associated data collection and processing  
can be found at:  
  
https://www.psychtoolbox.net/data-protection  
  
Once a license has been activated online, you can use the Psychtoolbox  
mex files offline for a limited number of days without an active internet  
connection. After this offline period, the mex files will stop working  
until an internet connection is reestablished. During each startup,  
Psychtoolbox will inform you of the remaining days of offline use before  
your computer must connect to the internet while Psychtoolbox is running.  
Each successful connection to the license servers will reset the offline  
use period to its maximum duration. When connected to the internet,  
Psychtoolbox will sync with the server at the first use in a session and  
periodically every few hours.  
  
  
# Subfunctions and their meaning  
  
[PsychLicenseHandling](PsychLicenseHandling)('Setup');  
- Informs the user about the purpose of license management, asks them for  
consent to enable license management, and performs initial setup to get  
to working mex files for license managed Psychtoolboxes. This function  
can be manually called by users, but by default it is called by the  
Psychtoolbox setup/install/update routines to automate license onboarding.  
  
[PsychLicenseHandling](PsychLicenseHandling)('Activate' [, licenseKey]);  
- Activate a paid license on a machine + operating system combination.  
This can either use a previously enrolled license key from earlier calls  
of [PsychLicenseHandling](PsychLicenseHandling)('Activate') or [PsychLicenseHandling](PsychLicenseHandling)('Setup'), or  
providing a new license key to activate the machine with a new license,  
by providing the new key in a string as optional 'licenseKey' parameter.  
  
This function can also be used if your machine was offline longer than  
allowed and your local activation needs to be refreshed, or if your old  
license has expired, or been suspended for some reason, then been resumed  
or extended by you, and you need Psychtoolbox to refresh its view of the  
current licensing state. If things don't work for some licensing related  
reason, calling [PsychLicenseHandling](PsychLicenseHandling)('Activate') may fix many problems.  
  
[PsychLicenseHandling](PsychLicenseHandling)('Deactivate');  
- Deactivate a currently activated machine + operating system combination,  
for the purpose of freeing up one activation, so a different machine +  
operating system combination can be activated instead. This allows you to  
"shift around" which machines can be used if your license only allows a  
limited number of simultaneous activations on a limited number of  
machines, and you temporarily have more machines than available  
activations.  
  
[PsychLicenseHandling](PsychLicenseHandling)('WipeLicense');  
- Deactivate a license on a machine and wipe the license key permanently  
if you don't intend to use that license on this machine anymore, e.g., if  
you are about to decomission a machine, or no longer use that license.  
  
active = [PsychLicenseHandling](PsychLicenseHandling)('IsLicensed' [, feature]);  
- Check if this installation of Psychtoolbox currently has a valid and  
active license, and possibly print some information about the licensing  
status, e.g., license expiry date, or how long the machine can still be  
used offline. If the optional 'feature' parameter is provided as a name  
string, then checks if that specific subfeature is enabled by the  
currently active license.  
  
[PsychLicenseHandling](PsychLicenseHandling)('AuthenticationToken');  
- Print an authentication token which allows you to prove that your  
machine has a properly paid, valid and active license associated with it.  
Our professional support personnel may ask you to provide such a token in  
some cases.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychLicenseHandling.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychLicenseHandling.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychLicenseHandling.m</code>
</div>

