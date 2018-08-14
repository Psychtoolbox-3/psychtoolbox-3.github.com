# [QuestUpdate](QuestUpdate)
##### >[Psychtoolbox](Psychtoolbox)>[Quest](Quest)

q=[QuestUpdate](QuestUpdate)(q,intensity,response)  
  
Update the struct q to reflect the results of this trial. The historical  
records q.intensity and q.response are always updated, but q.pdf is only  
updated if q.updatePdf is true. You can always call [QuestRecompute](QuestRecompute) to  
recreate q.pdf from scratch from the historical record.  
  
See Quest.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/Quest/QuestUpdate.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/Quest/QuestUpdate.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/Quest/QuestUpdate.m</code>
</div>

