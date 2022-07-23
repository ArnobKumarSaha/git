## add, commit
A single commit should only combine changes from the same topic.
To achieve this, stage the files carefully with `git add file_name` command.
If some file contains changes on multiple topic, use `git add -p file_name`. this will show a promt to select or not a partical changes for `add`.

## log
`git log --oneline --graph`. To see only the commit message, oneline is very useful.

`git log --grep="refactor" --before="2021-07-05" --auther="arnob"` will show all the commits that have 'refactor' in that message & commited before 5th july,21 by arnob.

`git log -- readme.md` will show the commits those are associated with readme.md file.

`git log feature..master` will show all the commits that are in master, but not in feature.

## [merge](cmds/merge.md)

## [rebase](cmds/rebase.md)

## pull

## push

## cherry-pick
For example, you accidentally commited into the `master`. Now to take that commit into `feature`, run `git cherry-pick <commit-hash>` from feature_branch. 
Clean up the master with `git reset --hard HEAD~1`.

## stash

## reset
`git reset --hard <commit-hash>` will throw out all the commits after the given commit-hash.
`git reset --hard HEAD~N` will throw out last N commits.

## reflog
This is the live git history. For example, you ran disastrous command which you shouldn't run. Now to undo, copy the last commit hash before your dangerous command. & run `git branch new_branch <commit-hash>`. This new branch is in the undo state. 

This will also word on branches too.

## submodule

## others
`git mergetool` is a nice tool to resolve conflicts.



<br>
<br>

# Resources
[basics ideology](https://www.youtube.com/watch?v=Uszj_k0DGsg&ab_channel=freeCodeCamp.org)

[sysdevbd repo](https://github.com/sysdevbd/sysdevbd.github.io/tree/master/git)

[Corey Schafer playlist](https://www.youtube.com/playlist?list=PL-osiE80TeTuRUfjRe54Eea17-YfnOOAx)

[Merge Vs Rebase](https://www.youtube.com/watch?v=CRlGDDprdOQ&ab_channel=Academind)

[advanced by freecodecamp](https://www.youtube.com/watch?v=qsTthZi23VE&ab_channel=freeCodeCamp.org)
