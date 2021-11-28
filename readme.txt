
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


GITHUB Pages can be used for -
   * free hosting of  public site 
   * hosting of static website like one in S3 bucket
   * publish/host doc  ( IN this eg we saw hosting a UserGuide docs)  
     We ust need to designate a branch('gh-pages' here) and point to an index.html page
   * For Documentation MkDocs or Sphinx can be used
   * For test result publish as Dashboard
   * For Project Roadmap
   
 