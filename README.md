Commands are sorted in alphabetical order.

## add
A single commit should only combine changes from the same topic.
To achieve this, stage the files carefully with `git add file_name` command.
If some file contains changes on multiple topic, use `git add -p file_name`. this will show a promt to select or not a partical changes for `add`.

## branch

## checkout

## cherry-pick
For example, you accidentally commited into the `master`. Now to take that commit into `feature`, run `git cherry-pick <commit-hash>` from feature_branch. 
Clean up the master with `git reset --hard HEAD~1`.

## commmit
`git commit --amend -m "commit_message"` to change the last commit msg.

## fetch

## log
`git log --oneline --graph`. To see only the commit message, oneline is very useful.

`git log -N` will show last N commits.

`git log --grep="refactor" --before="2021-07-05" --auther="arnob"` will show all the commits that have 'refactor' in that message & commited before 5th july,21 by arnob.

`git log -- readme.md` will show the commits those are associated with readme.md file.

`git log feature..master` will show all the commits that are in master, but not in feature.

## [merge](cmds/merge.md)

## pull

## push

## [rebase](cmds/rebase.md)


## reflog
This is the live git history. For example, you ran disastrous command which you shouldn't run. Now to undo, copy the last commit hash before your dangerous command. & run `git branch new_branch <commit-hash>`. This new branch is in the undo state. 

## reset
`git reset --hard <commit-hash>` will throw out all the commits after the given commit-hash.
`git reset --hard HEAD~N` will throw out last N commits.

`git reset --mixed HEAD~N` will throw out the commits, but not changes. All the local changes & the changes of the throw-out commits will still remain (in `unstaged` status). This is the default.

`--soft` is almost like `--mixed`. Nut all the local changes & the change of the throw-out commits will still be there on `staged` status.

Info: `HEAD~1` is same as `HEAD^`. `git reset HEAD` will throw 0 commits (so head remains same), just the local changes.

## restore
use case : Let, you make some changes & have not commited yet. Now, you want to clear up the changes of a file & bring that into state of the last commit. `git restore file_name`. NB : It will not be undone. Use `git restore .` to discard all local changes,

Similiarly, if you deleted the file & now want to bring it back (as like as last commmit), use the same above command.

Use `git restore -p file_name` to either keep or discard the chnages of the file one-by-one. (p for patch). 

This will also word on branches too.

## revert
To throw up the changes of an older commit, run `git revert <older_commit_hash>`. This will make another commit which will contain the exact opposite changes of our given commit.

## stash

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

[Undo mistakes](https://www.youtube.com/watch?v=lX9hsdsAeTk&ab_channel=freeCodeCamp.org)

[advanced by freecodecamp](https://www.youtube.com/watch?v=qsTthZi23VE&ab_channel=freeCodeCamp.org)
