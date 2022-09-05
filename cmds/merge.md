When merging, if one branch has no new commit, then it is called `fast forward` merge. In this case, git doesn't create the merge-commit.

from master, `git merge --squash feature` will sqaush all the commits of feature branch into one commit & will put that on top of the last commit of master.  

`git merge --abort` to undo everything & start fresh

To merge a remote branch with local : `git merge origin/<remote_branch_name>`