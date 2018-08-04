# [Shuffle](Shuffle)
##### >[Psychtoolbox](Psychtoolbox)>[PsychProbability](PsychProbability)

 [Y,index] = [Shuffle](Shuffle)(X [, bindDim])  
  
 Randomly sorts X.  
  
 If X is a vector, sorts all of X, so Y = X(index).  
 If X is an m-by-n matrix, sorts each column of X, so  
    for j=1:n, Y(:,j)=X(index(:,j),j).  
  
 The optional 'bindDim' parameter allows this function to shuffle with the  
 same order across the bindDim. It also work with higher dimension arrays.  
 for example, if you have an n by m matrix X and hope shuffle each column  
 with same random order ([Shuffle](Shuffle) the rows), rather than shuffle each  
 column independently, you can run [Shuffle](Shuffle)(X, 2). This function also works  
 on higher dimension arrays. say a 3-d array, If you bind the 2nd  
 dimension, it will shuffle the rows on each page independently. If I bind  
 the 2nd and 3rd dimension, then it will shuffle the layer of the 3-d  
 array.  
  
###  Examples:  
  
 create a 2-d array:  
   x = repmat((1:4)',1,5)  
  
 [Shuffle](Shuffle) each column of x independently:  
   y1 = [Shuffle](Shuffle)(x)  
  
 [Shuffle](Shuffle) columns of x with same order:  
   y2 = [Shuffle](Shuffle)(x,2)  
  
 Create a 3-d array (4 by 5 by 3), each column contains a vector [1:4]'  
   x = reshape(repmat(reshape(kron([1,1,1],1:4),4,3),5,1),4,5,3)  
  
 [Shuffle](Shuffle) each column independently on each page:  
   [y,ind]=[Shuffle](Shuffle)(x)  
  
 [Shuffle](Shuffle) 1\*5 rows independently on each page:  
   [y,ind]=[Shuffle](Shuffle)(x,[2])  
  
 [Shuffle](Shuffle) 1\*1\*3 rows independently on each column:  
   [y,ind]=[Shuffle](Shuffle)(x,[3])  
  
 Create a 3-d array (3 by 4 by 5), each row contains a vector [1:4]  
   x = reshape(repmat(reshape(kron(1:4,[1,1,1]),3,4),1,5),3,4,5)  
  
 [Shuffle](Shuffle) 3\*1\*5 page along the 2nd dimension:  
   [y,ind]=[Shuffle](Shuffle)(x,[1,3])  
  
 This is same as:  
   y2 = [RandDim](RandDim)(x,2)  
   x = reshape(repmat(reshape(repmat(reshape(kron(1:4,[1,1,1]),3,4),1,5),3,4,5),1,2),3,4,5,2)  
   [y,ind]=[Shuffle](Shuffle)(x,[1,3])  
  
 Also see SORT, [Sample](Sample), [Randi](Randi), [RandDim](RandDim), and [RandSample](RandSample).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychProbability/Shuffle.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychProbability/Shuffle.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychProbability/Shuffle.m</code>
</div>

