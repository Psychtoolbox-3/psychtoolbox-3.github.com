# [AddNormalsToOBJ](AddNormalsToOBJ)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

obj = [AddNormalsToOBJ](AddNormalsToOBJ)(obj [, flipDir=0]);  
Adds surface normal vectors to the vertices of the given input 'obj' 3D  
object representation, returns the new 'obj' with added vertex normal  
vectors. If the input 'obj' already has normal vectors assigned, these  
are overwritten!  
  
The optional parameter 'flipDir' defines if the direction of the computed  
normal vectors should be flipped by 180 degrees. Effectively, it selects  
which side of the triangle is considered to be the "outside" - the direction  
into which the normal vector should point.  
  
The employed algorithm only works on triangles, not on quads. It computes  
a per-triangle normal vector via normalized cross-product computation among  
the edges of the triangle. Then it distributes those normals to the 3  
vertices that define the triangle, accumulating contributions of all  
triangles that share a vertex. At the end, the accumulated normals are  
normalized and assigned as per-vertex normals.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/AddNormalsToOBJ.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/AddNormalsToOBJ.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/AddNormalsToOBJ.m</code>
</div>

