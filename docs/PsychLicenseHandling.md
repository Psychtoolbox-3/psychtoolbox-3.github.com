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
are provided by our commercial host company, the Medical Innovations  
Incubator [GmbH](GmbH), as of December 2024. Contact details are as follows:  
  
Medical Innovations Incubator [GmbH](GmbH)  
Eisenbahnstr. 63  
72072 Tübingen  
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
  
If your local environments firewall prevents online license management from  
working, see the section at the bottom for how to add firewall exception rules  
to make it work anyway. Below that section you will also find instructions for  
operating in a fully offline "air gapped" environment without any internet access.  
The latter may require specially configured licenses, as our default licenses do  
not support fully offline use.  
  
# Subfunctions and their meaning  
  
[PsychLicenseHandling](PsychLicenseHandling)('Setup');  
- Informs the user about the purpose of license management, asks them for  
consent to enable license management, and performs initial setup to get  
to working mex files for license managed Psychtoolboxes. This function  
can be manually called by users, but by default it is called by the  
Psychtoolbox setup/install/update routines to automate license onboarding.  
  
[PsychLicenseHandling](PsychLicenseHandling)('SetupLicense');  
- Like 'Setup', but always prompts for a new license key, even if a key  
is already enrolled, or a trial is active at the moment.  
  
[PsychLicenseHandling](PsychLicenseHandling)('SetupGlobal');  
- This behaves mostly like 'Setup', but it is meant for system administrators  
or IT personnel to create a global configuration file to express consent to  
license management on behalf of all users of this Psychtoolbox installation,  
and also to store a license key for automatic node activation. The global  
configuration file will be stored in the Psychtoolbox main folder, ie. the  
folder printed by the [PsychtoolboxRoot](PsychtoolboxRoot)() function. You can use this function  
if you use disc imaging software or similar provisioning tools to install and  
setup a Psychtoolbox installation once as part of a provisioning image, then  
clone the provisioning image and Psychtoolbox installation to many physical  
machines. The global config file will cause each Psychtoolbox on each of the  
provisioned machines to activate and setup license management and activate that  
node at first use of Psychtoolbox.  
  
[PsychLicenseHandling](PsychLicenseHandling)('Activate' [, licenseKeyOrUserCredential]);  
- Activate a paid license on a machine + operating system combination.  
This can either use a previously enrolled license key from earlier calls  
of [PsychLicenseHandling](PsychLicenseHandling)('Activate') or [PsychLicenseHandling](PsychLicenseHandling)('Setup'), or  
providing a new license key to activate the machine with a new license,  
by providing the new key in a string as optional 'licenseKeyOrUserCredential'  
parameter. Instead of a license key, one can also enter the login credentials  
of a user account with associated license key, to fetch the associated key  
automatically, e.g., if the account is jon.doe@doeland.us with password oink,  
then the credentials would be the following text: jon.doe@doeland.us:oink  
  
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
  
[PsychLicenseHandling](PsychLicenseHandling)('News');  
- Print latest stored news about Psychtoolbox, and also specifically related to  
this license and activations. Psychtoolbox prints those messages automatically  
once when they are new. This function will print them even if they have been  
printed before.  
  
  
# USE IN STRICTLY FIREWALLED ENVIRONMENTS  
  
If your firewall is blocking internet connections to our license servers,  
you can configure it as follows to allow connecting to the license servers.  
Follow the most recent instructions on this website for passthrough for EU data centers:  
  
https://docs.cryptlex.com/node-locked-licenses/proxies-and-firewall\#for-our-eu-data-center  
  
As of March 2025, the following configuration would be needed, but check above  
website for up to date informations if in doubt:  
  
### The following IP addresses and URL should be whitelisted:  
  
   IP Addresses to Whitelist:  
       75.2.113.112  
       99.83.149.57  
  
   Web API URL to Whitelist:  
       https://api.eu.cryptlex.com:443  
  
# OFFLINE USE IN AIR GAPPED ENVIRONMENTS  
  
Some non-standard software subscription licenses allow offline activation and  
deactivation by use of the customer portal and passing forth and back offline  
activation and deactivation request and response files. This allows use in air-  
gapped environments without access to the public internet or to our license  
servers. If your purchased license supports this, the functions are as follows:  
  
[PsychLicenseHandling](PsychLicenseHandling)('ActivateEnrolledKeyOffline', pathToOfflineRequestResponseFile);  
- Either create an offline activation request file under the specified path/filename,  
which allows creation of an offline activation response file in the customer portal,  
or reads such an offline activation response file and activates your local machine.  
  
E.g., after enrolling a license key via [PsychLicenseHandling](PsychLicenseHandling)('Setup') or  
[PsychLicenseHandling](PsychLicenseHandling)('Activate', licenseKey); do the following:  
  
1. [PsychLicenseHandling](PsychLicenseHandling)('ActivateEnrolledKeyOffline', 'offlineRequest.dat');  
  
2. Login to customer portal and upload 'offlineRequest.dat' to create offline  
   response file, downloaded to the file 'offlineResponse.dat'.  
  
3. [PsychLicenseHandling](PsychLicenseHandling)('ActivateEnrolledKeyOffline', 'offlineResponse.dat') to  
   activate this machine.  
  
[PsychLicenseHandling](PsychLicenseHandling)('DeactivateEnrolledKeyOffline', pathToOfflineProofFile);  
- Deactivate the machine locally and write a deactivation proof file into the  
path/filename 'pathToOfflineProofFile'. You can upload that proof file into  
the customer portal to deactivate the machine in the license servers, so the  
machine activation that has been freed up can be reused on a different machine.  
Not all licenses allow offline deactivation of once activated machines.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychLicenseHandling.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychLicenseHandling.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychLicenseHandling.m</code>
</div>

