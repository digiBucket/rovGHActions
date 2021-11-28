
 USER GUIDE documentation 
 Here the codebase has one UserGuide.md (markdown) file.
 We need to Trigger the Release workflow only if this UserGuide doc is modified 
    to ascertain that the UserGuide remains updated always
 
 create 1 workflows-
 JOB 1 - Build
 JOB 2 - Documentation 

  We 
  Create a dir(docs) in runner
  Convert markdown file into HTML-> using PANDOC (an opensource & comes in a Docker container)
  Rename the converted md as index.html and place in the folder(docs)
  Deploy this to GitHub pages using community actions

 After running the WorkFlow & doc is published, 
    in GitHub GOTO - Settings>Pages>Source - pick 'gh-pages' - SAVE
    Now refresh to see the URL. This URL shows the UserGuide



 