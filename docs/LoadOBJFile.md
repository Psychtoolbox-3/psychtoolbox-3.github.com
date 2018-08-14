# [LoadOBJFile](LoadOBJFile)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

objobject=[LoadOBJFile](LoadOBJFile)(modelname [, debug] [, preparse])  
  
Load an Alias/Wavefront ASCII-OBJ file and return description of corresponding 3D  
models in 'objobject'. The current implementation will only consider polygons  
with 3 or 4 vertices per polygon, corresponding to [OpenGL](OpenGL) GL\_TRIANGLES or GL\_QUADS.  
The routine can only parse ASCII OBJ files, not the (more disk space efficient)  
binary files. It will also ignore any part of the OBJ specification that is not a  
polygon mesh, e.g., NURBS. It will also ignore any kind of .mtl material/texture  
definition files.  
  
Parameters:  
'modelname' Filename of the OBJ file to read.  
'debug' (Optional) If set to non-zero, some debug output is written to the Matlab prompt.  
'preparse' (Optional) If set to non-zero (default), some preparsing is  
done to speed up loading of large OBJ files. Preparsing assumes that all  
vertices, texture coordinates and face indices contain 3 components. If  
loading of your OBJ file fails, retry with preparse==0 to use a more  
generic but slow loader.  
  
Return values:  
'objobject' objobject is a cell array of structs. For each mesh in the  
OBJ file, a single cell is created in objobject. Each cell contains a  
struct whose subfields contain all information about the mesh. A struct  
consists of the following fields:  
  
faces == 3-by-count or 4-by-count elements index matrix: Each of the 'count' columns  
defines one of 'count' polygons. Each polygon is defined by an integer index into  
the vertices, normals, texcoords arrays. Polygons can be triangles or quadrilaterals.  
  
vertices == A m-by-n vector of vertex position definitions: Each of the n columns  
defines the position of one of n vertices. m Can be 2 for 2D points, 3 for 3D points  
or 4 for 3D points with additional 'w' component.  
  
texcoords == Optional 2-by-n vector of texture coordinates.  
  
normals == Optional 3-by-n vector of surface normals.  
  
If a mesh contains triangle-definitions and quad-definitions, the triangle  
definitions will be returned in 'faces' whereas the Quads will be returned in  
'quadfaces'. If only one type of primitives is defined, it will always be returned  
in 'faces'. It is possible but uncommon for a OBJ file to not contain 'faces' at all.  
  
subMeshName = String with the name of the sub-mesh stored in cell, as  
defined by the 'g' (geometry group) parameter. Can be empty if no  
explicit group names are defined.  
  
mtllib = Name of the .mtl material library definition file which contains  
things like textures and rendering parameters for the object. Can be  
empty if no such file is defined.  
  
usemtl = Cell array of material selectors. Can be empty, or have  
arbitrarily many cells. Each cell defines which material from the  
material library file 'mtllib' should be selected for rendering a subset  
of the quad- or triangle-faces in a submesh. Each cell has these  
subfields:  
  
   materialName   = String with name of material to select from mtllib.  
  
   triStartIndex  = Startindex (Starting with 0 for first element) of the  
                    first triangle face to render with given materialName.  
  
   quadStartIndex = Startindex (Starting with 0 for first element) of the  
                    first quad face to render with given materialName.  
  
  
Example: Assuming the OBJ file contains exactly one triangle mesh, you'll  
be able to access its data as: objobject{1}.faces --\> faces of the mesh,  
objobject{1}.vertices --\> vertex definitions, ...  
  
nobjects = length(objobject); Will return the number of meshes in the OBJ  
file in 'nobjects'. objobject{i}.vertices would return the vertex  
definition array of the i'th mesh in the OBJ file.  
  
  
This loader is an improved/modified version of the loader from MATLAB-Central, written by:  
W.S. Harwin, University Reading, 2006  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/LoadOBJFile.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/LoadOBJFile.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/LoadOBJFile.m</code>
</div>

