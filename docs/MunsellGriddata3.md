# [MunsellGriddata3](MunsellGriddata3)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)>[PsychMunsell](PsychMunsell)

 [w,X,tri] = [MunsellGriddata3](MunsellGriddata3)(x,y,z,v,xi,yi,zi,method,options,X,tri)  
  
 This is a modified version of the Matlab function griddata3.  We modified  
 to allow precomputing of the triangulation, and then direct use of that.  
 This will allows us to precompute the triangulation (slow) and  
 then interpolate using the same triangulation many times (fast, we hope).  
  
GRIDDATA3 Data gridding and hyper-surface fitting for 3-dimensional data.  
   W = GRIDDATA3(X,Y,Z,V,XI,YI,ZI) fits a hyper-surface of the form  
   W = F(X,Y,Z) to the data in the (usually) nonuniformly-spaced vectors  
   (X,Y,Z,V).  GRIDDATA3 interpolates this hyper-surface at the points  
   specified by (XI,YI,ZI) to produce W.  
  
   (XI,YI,ZI) is usually a uniform grid (as produced by MESHGRID) and is  
   where GRIDDATA3 gets its name.   
  
   [...] = GRIDDATA3(X,Y,Z,V,XI,YI,ZI,METHOD) where METHOD is one of  
       'linear'    - Tessellation-based linear interpolation (default)  
       'nearest'   - Nearest neighbor interpolation  
  
   defines the type of surface fit to the data.   
   All the methods are based on a Delaunay triangulation of the data.  
   If METHOD is [], then the default 'linear' method will be used.  
  
   [...] = GRIDDATA3(X,Y,Z,V,XI,YI,ZI,METHOD,OPTIONS) specifies a cell   
   array of strings OPTIONS to be used as options in Qhull via DELAUNAYN.  
   If OPTIONS is [], the default options will be used.  
   If OPTIONS is {''}, no options will be used, not even the default.  
  
   Example:  
      rand('state',0);  
      x = 2\*rand(5000,1)-1; y = 2\*rand(5000,1)-1; z = 2\*rand(5000,1)-1;  
      v = x.^2 + y.^2 + z.^2;  
      d = -0.8:0.05:0.8;  
      [xi,yi,zi] = meshgrid(d,d,d);  
      w = griddata3(x,y,z,v,xi,yi,zi);  
   Since it is difficult to visualize 4D data sets, use isosurface at 0.8:  
      p = patch(isosurface(xi,yi,zi,w,0.8));  
      isonormals(xi,yi,zi,w,p);  
      set(p,'FaceColor','blue','EdgeColor','none');  
      view(3), axis equal, axis off, camlight, lighting phong  
  
   Class support for inputs X,Y,Z,V,XI,YI,ZI: double  
  
   See also GRIDDATA, GRIDDATAN, QHULL, DELAUNAYN, MESHGRID.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/PsychMunsell/MunsellGriddata3.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/PsychMunsell/MunsellGriddata3.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/PsychMunsell/MunsellGriddata3.m</code>
</div>

