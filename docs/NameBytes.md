# [NameBytes](NameBytes)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

bytesName=[NameBytes](NameBytes)(numBytes [,abbreviateFlag])  
  
[NameBytes](NameBytes) accepts a quantity of bytes and returns a string naming that number  
of bytes in more readable form.  For example:  
  
    \>\> c=[Screen](Screen)('Computer');  
    \>\> c.hw.physmem  
  
    ans =  
  
       1.3422e+09  
  
    \>\> [NameBytes](NameBytes)(c.hw.physmem)  
  
    ans =  
  
    1.25 GB  
  
    \>\>  
  
### Numbers of bytes have the following names and abbreviations:  
  
  Byte        B       2^0                                     1        
  [KiloByte](KiloByte)    KB      2^10                                1,024  
  [MegaByte](MegaByte)    MB      2^20                            1,048,576  
  [GigaByte](GigaByte)    GB      2^30                        1,073,741,824  
  [TeraByte](TeraByte)    TB      2^40                    1,099,511,627,776     
  [PetaByte](PetaByte)    PB      2^50                1,125,899,906,842,624  
  [ExaByte](ExaByte)     EB      2^60            1,152,921,504,606,846,976  
  [ZettaByte](ZettaByte)   ZB      2^70        1,180,591,620,717,411,303,424  
  [YottaByte](YottaByte)   YB      2^80    1,208,925,819,614,629,174,706,176  
  
By default [NameBytes](NameBytes) uses the abbeviated byte quantity label, for   
example "GB" instead of "[GigaBytes](GigaBytes)".  For the full name, pass  
1 in the optional abbreviateFlag argument.    
  
see also: [NameFrequency](NameFrequency), [DescribeComputer](DescribeComputer)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/NameBytes.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/NameBytes.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/NameBytes.m</code>
</div>

