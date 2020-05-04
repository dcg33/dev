https://devconnected.com/how-to-clone-a-git-repository/

Initial:
#git init 
#git remote add origin https://github.com/dcg33/dev.git

git clone https://github.com/dcg33/dev.git
mkdir terraform
cd terraform/
echo "# dev" >> README.md
git commit -am "added readme"
git remote add origin https://github.com/dcg33/dev.git
git push -u origin master

Branching:
git clone -b feature2 https://github.com/dcg33/dev.git
git branch #ensure feature2 is the cloned branch

Merging: 

	Method 1: Using branch to remote https://devconnected.com/how-to-push-git-branch-to-remote/
 git checkout feature3
 vi README.md > feature3
 git commit -am "added f3"
 git push origin feature3
 git show-branch
  feature2
  feature3
    git checkout feature3
    git show
    git pull
    git checkout feature3
    git merge origin/feature2
    git push origin feature3:feature2
	
	Method 2: Using git merge
	First we roll back:
	https://devconnected.com/how-to-undo-last-git-commit/
	https://devconnected.com/how-to-git-reset-to-head/
 git checkout feature2
 cat README.md > feature3 is in feature3 from method1
 git log 	
	$ git log
commit fa2ee0c1c6e09bbd5729f5d1e4c77265f3e67113 (HEAD -> feature2, origin/feature3, origin/feature2, feature3)
Author: dcg1 <dobrescu.cristian@gmail.com>
Date:   Wed Apr 15 13:53:16 2020 +0300

    added feature3

commit ae8d1244059a2cd3a6b43e6e82365ed9f21d0d02
Author: dcg1 <dobrescu.cristian@gmail.com>
Date:   Wed Apr 15 13:38:33 2020 +0300

    added f3

commit 90f9925d8afdf3b4bd5e429e2b163c3a937529a7 (origin/feature1)
Author: dcg1 <dobrescu.cristian@gmail.com>
Date:   Wed Apr 15 13:11:09 2020 +0300

    edited readme

commit d083689961965dffcf2d2a02559c33c0c4a97ca8
Author: dcg1 <dobrescu.cristian@gmail.com>
Date:   Wed Apr 15 13:07:49 2020 +0300

    Added readme/terraform
	
$ git reset --hard 90f9925d8afdf3b4bd5e429e2b163c3a937529a7
HEAD is now at 90f9925 edited readme

git add .
git commit -m "force rollback to feature2"
git push origin feature2 --force
git show

	$ git show
commit 90f9925d8afdf3b4bd5e429e2b163c3a937529a7 (HEAD -> feature2, origin/feature2, origin/feature1)
Author: dcg1 <dobrescu.cristian@gmail.com>
Date:   Wed Apr 15 13:11:09 2020 +0300

    edited readme

diff --git a/terraform/README.md b/terraform/README.md
index 3a93c8b..f1374d4 100644
--- a/terraform/README.md
+++ b/terraform/README.md
@@ -1 +1 @@
-# dev
+# dev f2
 Next we merge:
 https://stackabuse.com/git-merge-branch-into-master/
 
$ git branch new-branch
$ git branch
* master
new-branch
$ git checkout new-branch
Switched to branch ‘new-branch'
$ git branch
master
* new-branch

# ...develop some code...

$ git add –A
$ git commit –m "Some commit message"
$ git checkout master
Switched to branch 'master'
$ git merge new-branch

In case of merge conflicts:
# Switch to the topic branch:

git checkout branch

# Create a merge commit, which looks as if it's merging in from master, but is actually discarding everything from the master branch and keeping everything from branch:

git merge -s ours master

# Switch back to the master branch:

git checkout master

# Merge the topic branch into master - this should now be a fast-forward that leaves you with master exactly as branch was:
git merge branch 
https://intellipaat.com/community/21257/git-merge-error-you-need-to-resolve-your-current-index-first
test field

