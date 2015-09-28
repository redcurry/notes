Delete remote branch::

    git push origin :[remote_branch]

Cancel merge::

    git merge —abort

Undo a merge::

    git reset --merge ORIG_HEAD

Rebase w/ master::

    git fetch origin master
    git rebase origin/master

Push tags::

    git push —tags

Add new feature to project::

    git checkout -b branch_name
    [do commits]
    [master should be updated]
    git rebase -i master

Stash::

    git stash save "WIP: Comment"
    git stash pop

Search code in history::

    git grep <regexp> $(git rev-list <rev1>..<rev2>)
    -or-
    git grep <regexp> $(git rev-list --all)

Merge a repository into another (works for merging into empty repo);
project-a to project-b::

    cd path/to/project-b
    git remote add project-a path/to/project-a
    git fetch project-a
    git merge project-a/master
    git remote remove project-a

Pull with rebase instead of merge::

    git pull --rebase

Automatically rebase with pull in new branches::

    git config branch.autosetuprebase always

Configure to push tracked branches (not just matching branch names),
since local branches could track branches with the same name
from different remote repos::

    git config push.default tracking

Create and checkout an orphan branch::

    git checkout --orphan docs

Add a free form note at the HEAD of the current branch::

    git notes add -m “The note”

Cherry pick::

    git cherry-pick <commit_id>    # on branch to apply commits
    -or-
    git cherry-pick <commit_id1>..<commit_id2>    # apply a range of commits
                                                    (didn’t work)

Find most recent common ancestor between two branches::

    git merge-base <branch_1> <branch_2>

Clean everything that’s not tracked by the repository::

    git clean -fxd

Push an existing repository to a new (empty) remote repository::

    cd path/to/project
    git remote add origin <remote_address>:path/to/remote/project
    git push -u origin master

Revert a commit (creates a new commit)::

    git revert <commit_id>
