

1) Remove a file you accidentally committed in your last commit (but haven’t pushed yet) : `git reset - -soft HEAD^1` to remove certain files from a commit. Then `git rm --cached <file-name>`  to remove (`to untrack` more specifically) the file you don’t want to commit.  

2) Remove a file (that doesn't contain sensitive info) you already pushed to the git repository : `git rm - -cached name_of_file`  NB : will be found in github history.  This will also work folder removal : `git rm - -cached -r folder-name/` . Then remove your folder you dont want to push.

3) Remove a file (that contains sensitive info) you already pushed to the git repository : `git reset --mixed HEAD~N` where N=how many commit you want to uncommit.  

- - after these commands , use `git add` & `git commit` command as always.
- - force push could be needed for some cases.