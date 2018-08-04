# [Struct2Vect](Struct2Vect)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

vec = [Struct2Vect](Struct2Vect)(struc,fieldnm)  
Traverses array of structs STRUC and returns data from all fields FIELDNM  
in vector VEC.  
Returns array vector if field contains numeric scalars or scalar structs,  
cell vector otherwise. If concatenating struct arrays, each struct must  
contain the same fields  
  
Example: for field data.field:  
  data(1).field = 23;  
  data(2).field = 56;  
  vec = [Struct2Vect](Struct2Vect)(data,'field')  
  vec = [23 56];  
  
Example: for field data2.test:  
  data2(1).test = 23;  
  data2(2).test = 'd';  
  vec = [Struct2Vect](Struct2Vect)(data2,'test')  
  vec = {23 'd};  
  
Example: for field data3.cells:  
  data3(1).cells = 23;  
  data3(2).cells = [42 45];  
  vec = [Struct2Vect](Struct2Vect)(data3,'cells')  
  vec = {23, [42 45]};  
  
Example: for field data4.struc:  
  data4(1).struc.a = 24;  
  data4(2).struc.a = [42 45];  
  vec = [Struct2Vect](Struct2Vect)(data4,'struc')  
  vec(1).a = 24;  
  vec(2).a = [42 45];  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/Struct2Vect.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/Struct2Vect.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/Struct2Vect.m</code>
</div>

