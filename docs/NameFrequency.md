# [NameFrequency](NameFrequency)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

fName=[NameFrequency](NameFrequency)(fValue, [numDecimalPlaces])  
  
[NameFrequency](NameFrequency) accepts a frequency (in Hz) and returns a  
string naming that frequency in a more readable form.  For example:  
  
    \>\> c=[Screen](Screen)('Computer');  
    \>\> c.hw.cpufreq  
  
    ans =  
  
       999999997  
  
    \>\> [NameFrequency](NameFrequency)(c.hw.cpufreq)  
  
    ans =  
  
    1.00 [GHz](GHz)  
  
    \>\> [NameFrequency](NameFrequency)(c.hw.cpufreq,6)  
  
    ans =  
  
    999.999997 [MHz](MHz)  
  
    \>\>  
  
  
By default [NameFrequency](NameFrequency) displays two digits to the right of the decimal  
point. Specify other numbers of digits by passing the optional  
numDecimalPlaces argument.    
  
[NameFrequency](NameFrequency) is used by [DescribeComputer](DescribeComputer) to name the clock frequency of  
the CPU. For that purpose, it displays frequency to a specified number of  
decimal places, not to a specified precision.  It is therfore a poor  
choice for scientific work, where typcially a fixed precision in digits  
is appropriate.    
  
see also: [NameBytes](NameBytes), [DescribeComputer](DescribeComputer)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/NameFrequency.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/NameFrequency.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/NameFrequency.m</code>
</div>

