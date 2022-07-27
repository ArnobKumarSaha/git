
### Behind the scene :
Assume `c1` is the common ancestor of `feature` & `master`. `feature` has two new commit `c3` & `c5`. And `master` has two new commit `c2`, `c4`.
I am on `feature`, running `git rebase master`.
Behind the scene, there will be 3 steps:
1) remove the commits after the common ancestor (will not throw them away !)
2) applies the commits from `master`. After this step, both branch looks exactly the same.
3) applies the 'removed' commits of stage-1. N.B : the commit hash of these commits will be changed, as their parent is being changing. For example, `c3` had the parent `c1`, but now its parent is `c4`. We are changing the base, thats why it is called `rebase` !

After completion : `c1` -> `c2` -> `c4` -> `c3` -> `c5` 
So, Do not ise rebase on commits that you have already pushed on a shared repo.

### Interactive rebase : 
`git rebase -i HEAD~N` 
N is how far back in time do you wanna go (in other words, 'what should be the base commit') ? 
Using this interactive mode, we can change any commits message, delete, reorder, combine multiple commit into one, edit or split existing commit into multiple ones.N number of commits will be appeared in the interactive promt. There we only need to choose the keyword correctly.

For example, current commit history is c1->c2->c3->c4->c5, `c5` is head(latest). 

To change commit message of `c2` , run `git rebase -i HEAD~4`. set `reword` keyword in the c2 commit. Don't worry. The keywords & their meaning will be in the promt.

To combine c3 & c4 into one commit, `git rebase -i HEAD~3`. Set `squash` keyword on c4 commit. You can use `drop` keyword to delete a particular commit.

#### Adding changes to an old commit :: 
First add a new commit with 'fixup' prefix. `git commit --fixup <commit-hash>`. Then, run interactive rebase command with `--autosquash` option. And its done. nothing to do in the promt, git already have done our work !

One thing to keep in mind is, the interactive promt actually shows the commits in the reverse order of 'git log' output.

### extras :
`git rebase --abort` to undo everything & start fresh