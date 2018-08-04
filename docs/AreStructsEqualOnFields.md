# [AreStructsEqualOnFields](AreStructsEqualOnFields)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

areEqual = [AreStructsEqualOnFields](AreStructsEqualOnFields)(struct1,struct2,theFields)  
  
Returns 1 if two structs share the same value on each of the passed  
fields, 0 otherwise.  The equality of each field in the two structs is  
checked with a call to isequal()  
  
5/1/05     dhb, jmk   Handle cell and struct fields, a little bit.  
2012/06/12 DN         Can now handle fields of any data type supported by  
                      isequal(). Added some input checks  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/AreStructsEqualOnFields.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/AreStructsEqualOnFields.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/AreStructsEqualOnFields.m</code>
</div>

