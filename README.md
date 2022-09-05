Commands are sorted in alphabetical order.

## add
A single commit should only combine changes from the same topic.
To achieve this, stage the files carefully with `git add file_name` command.
If some file contains changes on multiple topic, use `git add -p file_name`. this will show a promt to select or not a partical changes for `add`.

`git add -A` (or --all) will stage all the files of the git repo. It doesn't make difference if it was run from a sub-directory or not. -A is the difault bahaviour of git add command.

`git add -u` (--update) will stage all the files except the untracked ones.
Also, don't use `git add *` as it is more linux specific & it can show unexpected behaviours for deleted & hidden files.

## branch
`git branch -m <old_name> <new_name>` to rename branches.
Use `-D` for force deletion, `-r` to list the remote branches only, & `-a` to see all branches.

## checkout
`git checkout -b <branch-name>` create & checkout to a branch.
`git checkout -- .` remove all the current-changes.

To create a local branch from a remote branch
`git checkout -b <local_branch_name> origin/<remote_branch_name>`

## cherry-pick
For example, you accidentally commited into the `master`. Now to take that commit into `feature`, run `git cherry-pick <commit-hash>` from feature_branch. 
Clean up the master with `git reset --hard HEAD~1`.

## clean
`git clean -df` will remove all the untracked directories and untracked filed.

## commmit
`git commit --amend -m "commit_message"` to change the last commit msg.

## config
`git config --global user.name "my_name"`. 'user.email' is also important to set.
`git config --list`

## diff

## fetch
`git fetch --all` to get the updated code from remote. It will not delete an already fetched remote branch from local (for example origin/feature1), even if it has been deleted in the actual repo. Use `--prune` to perform this type of complete syncup. 

## log
`git log --oneline --graph`. To see only the commit message, oneline is very useful.

`git log -N` will show last N commits.

`git log --grep="refactor" --before="2021-07-05" --auther="arnob"` will show all the commits that have 'refactor' in that message & commited before 5th july,21 by arnob.

`git log -- readme.md` will show the commits those are associated with readme.md file.

Use `git log --all file_name` to show all commits (commits inside a pr too). The above will show only the merged commits.
Add `--pretty=format:%H` option to only show the hashes.

`git log feature..master` will show all the commits that are in master, but not in feature.

## [merge](cmds/merge.md)

## pull

## push

## [rebase](cmds/rebase.md)


## reflog
This is the live git history. For example, you ran disastrous command which you shouldn't run. Now to undo, copy the last commit hash before your dangerous command. & run `git branch new_branch <commit-hash>`. This new branch is in the undo state. 

You could also checkout to a reflog-hash & then make branch from it. (you will be in detached HEAD for somethime though)

## reset
`git reset --hard <commit-hash>` will throw out all the commits after the given commit-hash.
`git reset --hard HEAD~N` will throw out last N commits.

`git reset --mixed HEAD~N` will throw out the commits, but not changes. All the local changes & the changes of the throw-out commits will still remain (in `unstaged` status). This is the default.  If you just run `git reset` this will be evaluated as `git reset --mixed HEAD`, which is simply unstaging  all the locally-changed files.

`--soft` is almost like `--mixed`. Nut all the local changes & the change of the throw-out commits will still be there on `staged` status. Note that, '--hard' doesn't work with untracked files. It keeps the untracked files as-it-is.

Info: `HEAD~1` is same as `HEAD^`. `git reset HEAD` will throw 0 commits (so head remains same), just the local changes.

## restore
use case : Let, you make some changes & have not commited yet. Now, you want to clear up the changes of a file & bring that into state of the last commit. `git restore file_name`. NB : It will not be undone. Use `git restore .` to discard all local changes,

Similiarly, if you deleted the file & now want to bring it back (as like as last commmit), use the same above command.

Use `git restore -p file_name` to either keep or discard the chnages of the file one-by-one. (p for patch). 

This will also word on branches too.

`git restore --source <revision-hash> file_name` to restore a file as it was in a particular revision. Look at `git log` to get the revision hash.

## revert
To throw up the changes of an older commit, run `git revert <older_commit_hash>`. This will make another commit which will contain the exact opposite changes of our given commit.

## stash
`git stash save "stash-message"`
`git stash apply stash@{x}`, set x accordingly. the stashed will be in the list though. Use `git stash pop` to also remove the stash.

stash@{0} is the most recent. bigger number means more older. `pop` pops up the recent. use `git stash drop <stash-id>` to drop a stash without applying it. `clear` to drop all.

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
