Git learning
===========================================

Basic commands
--------------

.. code:: bash

     # Set default global parameters
     git config --global user.email "you@example.com"
     git config --global user.name "Your Name"
     git config --global core.editor vim
     
     # Check the name of files that changed in two commits
     git diff --name-only SHA1 SHA2
     
     # Check url of remote repository:
     git remote -v
     # Change remote repository:
     git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
     # PUSH a local branch to remote branch
     git push <remote> <local_branch>:<remote_name>
     
     # Save temporarily changes
     git stash
     # Recover back
     git stash pop

     # Add .gitignore
     git rm -rf --cached .
     git add .gitignore


Remove commits before specific commit
-------------------------------------

.. code:: bash

   git checkout -b oldroot XXXX
   TREE=`git write-tree`
   COMMIT=`echo "Killed history" | git commit-tree "$TREE"`
   git checkout -b newroot "$COMMIT"
   git rebase --onto newroot oldroot master
   # repeat for other branches than master that should use the new initial commit
   git checkout master
   git branch -D oldroot
   git branch -D newroot
   git gc # WARNING: if everything's done right, this will actually 
   #delete your history from the repo!

Remove folder and its contents from git/GitHub’s history
--------------------------------------------------------------

.. code:: bash

   git filter-branch --tree-filter "rm -rf folder-name" --prune-empty HEAD
   git for-each-ref --format="%(refname)" refs/original/ | xargs -n 1 git update-ref -d
   git commit -m 'Removing folder-name from git history'
   git gc

Undo a commit
---------------

.. code:: bash

   git reset HEAD~1 #if you don't want your changes to be gone (unstaged changes). 
   # force pushing to delete the last commit on remote. 
   git push -f [origin] [branch]
