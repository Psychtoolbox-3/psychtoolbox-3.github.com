# [moglmorpher](moglmorpher)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

  
Matlab [OpenGL](OpenGL) Morpher - Performs linear morphs between different 3D shapes and  
renders the resulting shape via [OpenGL](OpenGL). Supports high-performance GPU  
based morphing on recent graphics hardware. Also performs linear morphing  
(linear combinations) between different texture images.  
  
The [moglmorpher](moglmorpher) computes linear combinations of shapes and their corresponding  
surface normal vectors and texture coordinate assignments. It then renders the  
resulting shape with its resulting surface normals and texture coordinates in  
an efficient way, using the [OpenGL](OpenGL) for Matlab (MOGL) functions.  
  
It also allows to render single sub-meshes efficiently, as well as  
predictions of screen space 2D (x,y) coordinates of vertices in the mesh.  
  
The whole setup for rendering (rigid orientation and position, camera view transforms,  
assignment and setup of textures or material properties, lighting, shaders, ...) is  
left to the calling parent routines, focusing solely on high performance morphing  
and rendering of generic triangle meshes. This allows for maximum flexibility.  
  
For a specific examples of usage, have a look at [MorphDemo](MorphDemo).m and  
[MorphTextureDemo](MorphTextureDemo).m.  
  
IMPORTANT: At the end of your script, you must call [moglmorpher](moglmorpher)('reset')  
to release all ressources and reset [moglmorpher](moglmorpher) into a well-defined  
state. Alternatively, you can call 'clear [moglmorpher](moglmorpher)', e.g., if your  
script aborted with an error. If your forget either of these, you'll see  
some weird error messages about "Invalid window record referenced"  
at invocation of the command.  
  
  
# Available subcommands and their meaning  
  
[moglmorpher](moglmorpher)('ForceGPUMorphingEnabled', enableflag);  
  
Forcefully enable or disable GPU based morphing. 'enableFlag'==1 -\>  
Forcefully enable, 'enableFlag'==0 --\> Forcefully disable.  
  
[moglmorpher](moglmorpher) can perform all morphing computations and rendering completely  
on the GPU on modern graphics hardware that supports this. This provides  
a significant speedup over morphing in Matlab/Octave code on the slower  
CPU. Normally, [moglmorpher](moglmorpher) auto-detects if GPU based morphing is possible  
and then enables that feature. If GPU morphing is not possible, it  
reverts to a slower Matlab CPU implementation of morphing. For GPU  
morphing, the Psychtoolbox imaging pipeline needs to be enabled by  
passing an optional valid non-zero 'imagingMode' flag to the  
[Screen](Screen)('OpenWindow', ...); call when opening the onscreen window. E.g.,  
the flag 'kPsychNeedFastOffscreenWindows' would enable the pipeline.  
  
There may be cases where either auto-detection goes wrong, or where you  
don't want to use GPU based morphing, e.g., if your hardware/gfx-driver  
is defective and GPU morphing doesn't work correctly, or if you want to  
use the [moglmorpher](moglmorpher)('renderNormals') subfunction which is not yet  
supported in GPU mode, or if you want to perform benchmarking of GPU vs.  
non-GPU mode. In such cases you can use this subfunction to manually  
enable/disable GPU based morphing, overriding the auto-detection code.  
  
It's important to call this function before the first invocation of any  
other subfunction!  
  
GPU based operation should be efficiently supported on all ATI Radeon  
X-1000 or later hardware and all [NVidia](NVidia) Geforce-6000 and later hardware.  
GPU based operation is not supported under [OpenGL](OpenGL)-ES1.x mobile/embedded  
[GPUs](GPUs).  
  
  
All following subfunctions must be only called when at least one onscreen  
window is open!  
  
  
meshid = [moglmorpher](moglmorpher)('addMesh', obj);  
-- Add a new shape to the collection of shapes to be morphed. 'obj'  
is a single struct that defines the object: Subfields are obj.faces,  
obj.vertices, obj.texcoords, obj.normals, obj.colors. Their meaning is  
the same as the corresponding parameters in the following 'addMesh'  
subcommand. The 'obj' syntax is provided for convenience, as 'obj' in the  
same format as provided by [LoadOBJFile](LoadOBJFile), i.e. obj =  
[LoadOBJFile](LoadOBJFile)('myfile.obj') will load the geometry in 'myfile.obj' into  
obj, which can then be passed to [moglmorpher](moglmorpher) via [moglmorpher](moglmorpher)('addMesh',  
obj{1}); to add the first mesh from 'myfile.obj' into the morpher.  
  
  
meshid = [moglmorpher](moglmorpher)('addMesh', faces, vertices [, texcoords] [, normals] [, colors]);  
-- Add a new shape to the collection of shapes to be morphed. faces == Index  
list that defines the topology of the shape: faces is a 3 by n vector. Each of  
the n columns defines one 3D triangle face, the 3 indices in the column are  
indices into the vertices, texcoords, colors and normals vectors that define the  
properties of the vertices.  
  
vertices == A 3-by-m vector that defines the shape of the object: Each of the  
m columns defines the 3D position of one of the corresponding m vertices.  
  
normals == A 3-by-m vector whose single columns define the (nx,ny,nz) components  
of unit normal surface vectors. The normals vector is optional and only needed if  
you want to do proper lighting calculations on your object.  
  
texcoords == A 2-by-m vector of 2D texture coordinates for each corresponding vertex.  
This vector is optional and only needed if you want to apply textures to the object.  
  
colors == A 3-by-m or 4-by-m vector whose single columns define the  
(red,green,blue [,alpha]) vertex color components of each vertex in  
'vertices' of unit normal surface vectors. The colors vector is optional  
and only needed if you want to do lighting calculations on your object.  
Most of the time you won't use vertex colors, but instead assign a  
texture for more flexibility and ease of use.  
Note: The current implementation doesn't support morphing of vertex  
colors. Instead it will simply use the vertex 'color' vector of the last  
added mesh for the morphed output -- a fixed assignment of vertex colors.  
  
The size and dimension of all provided vectors must match (==be identical) for all  
shapes. This is required, because otherwise the linear combination of shapes and  
normal vectors wouldn't be mathematically well defined.  
  
The function call returns a index for the mesh. The index is fixed for a  
given mesh unless you call [moglmorpher](moglmorpher)('deleteMeshAtIndex'), in which  
case the numbering may change. See 'deleteMeshAtIndex' for details.  
  
  
[moglmorpher](moglmorpher)('deleteMeshAtIndex', meshIndex [, dontReset=0]);  
-- Delete the mesh with index 'meshIndex' from the set of keyshapes. All  
keyshapes after the deleted meshIndex will "move down" one index. E.g.,  
if you delete the keyshape at meshIndex = 5, then the mesh with previous  
index 6 will become the new mesh with index 5, the mesh with old index 7 will  
become mesh 6 and so on. You have to take this renumbering into account  
for calls like [moglmorpher](moglmorpher)('renderMesh') that expect the meshid, and when  
passing in a morph 'weights' vector into the morphing functions, where  
the ordering of elements changes accordingly.  
  
'dontReset' optional: If set to 1 then [moglmorpher](moglmorpher) doesn't 'reset' itself  
when the last mesh is deleted. This saves overhead for reinit, but any  
new added mesh must have the exactly same topology as the previously  
deleted meshes, or bad things will happen.  
  
  
[moglmorpher](moglmorpher)('renderMesh', meshid);  
-- Render the mesh corresponding to the handle 'meshid'.  
  
  
oldEnable = [moglmorpher](moglmorpher)('assumeSparseMorphWeights', enable);  
-- Enable speed optimizations under the assumption that morph weight  
vector contains mostly zero weights, if 'enable' is set to 1. Otherwise  
optimize speed under the assumption of dense weight vectors. The default  
is to assume dense vectors, ie., 'enable' == 0.  
  
Two different algorithms are used, depending on the setting of this  
switch, which have different tradeoffs. However, switching settings here  
is cheap, so you could do it on a per-morph basis. The optimal choice may  
depend on complexity of your keyshape models and speed of your GPU, so  
your mileage will vary and you'll need to benchmark both options for  
optimal speed.  
  
  
[moglmorpher](moglmorpher)('renderMorph', weights [,morphnormals=1]);  
-- Compute a linear combination (a weighted average) of all stored meshes, as defined  
by the vector 'weights'. Render the final shape.  
For 'count' shapes, weight is a vector of length 'count'. The i'th scalar entry of weight  
is the coefficient used to integrate the i'th shape into the morph.  
  
  
[moglmorpher](moglmorpher)('computeMorph', weights [,morphnormals=1]);  
-- Same as 'renderMorph', just that rendering of the morphed shape is  
omitted. You can render the shape later by calling the 'render' subcommand.  
  
finalresult = sum\_for\_i=1\_to\_count(shape(i) \* weights(i));  
The shape (vertices) and normal vectors are linearly combined. The texture coordinates are  
not altered by the morph, neither are the vertex colors. If you set the  
optional argument morphnormals to zero, then normals are not touched by  
morphing either.  
  
  
[moglmorpher](moglmorpher)('render');  
-- Renders the last shape again. This is either the last rendered mesh or the last linear  
combination.  
  
  
glListHandle = [moglmorpher](moglmorpher)('renderToDisplaylist');  
-- Same as subcommand 'render', but the shape is not rendered as an image to the  
framebuffer, but stored to a new [OpenGL](OpenGL) display list. A unique 'glListHandle' to  
the new list is returned. Using this handle one can render the object  
later on via the command glCallList(glListHandle); and delete it via  
glDeleteLists(glListHandle, 1);  
  
Unsupported on [OpenGL](OpenGL)-ES.  
  
  
[moglmorpher](moglmorpher)('renderRange' [, startfaceidx=0] [, endfaceidx]);  
[moglmorpher](moglmorpher)('renderRangeToDisplayList' [, startfaceidx=0] [, endfaceidx]);  
-- Like 'render' and 'renderToDisplayList', except that the range of  
faces (triangles or quads) can be restricted to a subrange of the mesh.  
By default, the full mesh is rendered. 'startfaceidx' Allows start at  
given index instead of index zero. 'endfaceidx' Allows end at  
given index instead of the last face index in the mesh.  
  
Caution: Face indices count in units of surface primitives. 1 count = 1  
triangle or quad, depending on the type of your mesh.  
  
Caution: Face indices are zero-based! The first element is at index zero.  
This is different from the one-based indexing of vertices in the  
functions 'renderNormals' and 'getVertexPositions', where index 1 denotes  
the first vertex in the mesh.  
  
  
[moglmorpher](moglmorpher)('renderNormals' [,normalLength=1] [, startidx=1] [, endidx]);  
-- Renders the surface normal vectors of the last shape in green, either at unit-length,  
or at 'normalLength' if this argument is provided. This is a helper function for  
checking the correctness of computed normals. It is very slow!  
  
  
vpos = [moglmorpher](moglmorpher)('getVertexPositions', windowPtr [, startidx=1] [, endidx]);  
-- Compute and return a matrix which contains the projected screen space coordinates of all  
vertices that would be rendered when calling [moglmorpher](moglmorpher)('render'). windowPtr is the handle  
of the window into which we render. Optional arguments startidx and endidx define the  
index of the first vertex, resp. the last vertex to transform. The returned 'vpos' is a  
vcount-by-3 matrix, where vcount is the number of returned vertices, and row i contains the  
projected 3D position of the i'th vertex vcount(i,:) = (screen\_x, screen\_y, depth\_z);  
Unsupported on [OpenGL](OpenGL)-ES.  
  
count = [moglmorpher](moglmorpher)('getMeshCount');  
-- Returns number of stored shapes.  
  
  
textureCoordinates = [moglmorpher](moglmorpher)('getTexCoords');  
-- Returns current vector of textureCoordinates as used for rendering  
meshes.  
  
  
[vertices, normals] = [moglmorpher](moglmorpher)('getGeometry');  
-- Returns current vector of 'vertices' and (optionally) normals as used  
for rendering meshes. Call this after (at least one call to)  
'computeMorph' or 'renderMorph' to retrieve the current morphed mesh.  
vertices and normals are 3-by-n matrices, each column encoding the three  
components (x,y,z) of a single 3D vertex position or vertex normal.  
  
  
[texid, gltexid, gltextarget] = [moglmorpher](moglmorpher)('morphTexture', windowPtr, morphWeights, keyTextures);  
-- Compute a linear combination of the Psychtoolbox textures stored in  
vector 'keyTextures', using the values in vector 'morphWeights' as  
weights. Return handles to the computed (morphed) texture. 'texid' is a  
Psychtoolbox texture handle (e.g., for use with [Screen](Screen)('DrawTexture')),  
gltexid is an [OpenGL](OpenGL) texture handle and gltextarget is an [OpenGL](OpenGL) texture  
target. The texture could be used for rendering, e.g., onto a surface via  
glBindTexture(gltextarget, gltexid); and disabled again via  
glBindTexture(gltextarget, 0);  
  
Input textures must be rectangle textures and the output texture will be  
a rectangle texture. The morphed texture 'texid' is owned by [moglmorpher](moglmorpher).  
You must not close it or bad things will happen!  
  
  
[moglmorpher](moglmorpher)('reset');  
-- Resets the [moglmorpher](moglmorpher) - deletes all internal data structures.  
  
  
### CONTEXT MANAGEMENT FUNCTIONS:  
  
[moglmorpher](moglmorpher)() supports use of more than one morph context. This is useful  
if you have to morph multiple separate morph-models. You can create  
and setup one dedicated context for each such model. Then you can switch  
between contexts before executing [moglmorpher](moglmorpher)() commands. The commands  
will always apply to the current set context. Once you're done, you can  
delete contexts.  
  
Context switching is not free! It comes at a modest cost in terms of  
computation time spent if you have GPU based morphing enabled. It can  
consume significant time if you use software only morphing with models of  
non-trivial size.  
  
Use of these functions is optional. If you don't use them to create your  
own contexts, [moglmorpher](moglmorpher) will create a single default context and use  
that. This ensures backwards compatibility to old scripts and  
single-context scripts.  
  
### The following functions allow context management:  
  
context = [moglmorpher](moglmorpher)('createContext' [, windowPtr]);  
-- Create a new morphing context, attached to onscreen window 'windowPtr'  
- or the default window if 'windowPtr' is omitted. Return it in  
'context'. If you want to setup and then use the 'context', you will need  
to call 'setContext'.  
  
  
oldcontext = [moglmorpher](moglmorpher)('setContext', context);  
-- Set 'context' as the new morph context, return the previously set  
current context optionally in 'oldcontext'. All other [moglmorpher](moglmorpher)()  
commands always operate on the current morph context until you change the  
morphcontext to a new current morph context with this 'setContext'  
command. If you don't use 'setContext' in your scripts, [moglmorpher](moglmorpher) will  
automatically create and bind a default context for use. This ensures  
backwards compatibility to scripts which don't need multiple morph  
contexts.  
  
  
currentContext = [moglmorpher](moglmorpher)('getContext');  
-- Return the currently set morph context. If 'createContext' and  
'setContext' weren't used, this is the default context which was  
automatically created by [moglmorpher](moglmorpher).  
  
  
context = [moglmorpher](moglmorpher)('deleteContext', context);  
-- Delete given 'context' and release all its associated resources,  
return an emptied out copy in the optional return argument 'context'.  
  
IMPORTANT: You \*must\* delete all contexts with this method which have  
been created by 'createContext', otherwise you will leak resources!  
The exception is the currently bound context, which will get deleted  
automatically if [moglmorpher](moglmorpher)('reset'); is called, but not otherwise!  
  
If in doubt, call this on each of your contexts and then some...  
  
One convenient way to release all resources and clean out all contexts is  
to call "clear all", this will reset everything. However, do not use  
"clear all" inside scripts which are supposed to work within GNU/Octave!  
Only call at the command prompt.  
  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/moglmorpher.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/moglmorpher.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/moglmorpher.m</code>
</div>

