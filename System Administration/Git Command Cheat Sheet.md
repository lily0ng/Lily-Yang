

```
root@lilyang - git init
root@lilyang - Initialized empty Git repository in /home/lilyang/myproject/.git/
```

```
root@lilyang - git status
root@lilyang - On branch main
nothing to commit, working tree clean
```

```
root@lilyang - git add .
root@lilyang - (No output)
```

```
root@lilyang - git commit -m "Initial commit"
root@lilyang - [main (root-commit) abc1234] Initial commit
1 file changed, 10 insertions(+)
create mode 100644 README.md
```

```
root@lilyang - git log
root@lilyang - commit abc1234 (HEAD -> main)
Author: Lily Yang <lily@example.com>
Date:   Sat Nov 16 12:00:00 2025 +0630
    Initial commit
```

```
root@lilyang - git branch
root@lilyang - * main
```

```
root@lilyang - git branch develop
root@lilyang - (No output)
```

```
root@lilyang - git checkout develop
root@lilyang - Switched to branch 'develop'
```

```
root@lilyang - git checkout -b feature/login
root@lilyang - Switched to a new branch 'feature/login'
```

```
root@lilyang - git merge main
root@lilyang - Already up to date.
```

```
root@lilyang - git merge feature/login
root@lilyang - Merge made by the 'recursive' strategy.
 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

```
root@lilyang - git remote add origin https://github.com/lily/myproject.git
root@lilyang - (No output)
```

```
root@lilyang - git push -u origin main
root@lilyang - Counting objects: 3, done.
Writing objects: 100% (3/3), 250 bytes | 250.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/lily/myproject.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```

```
root@lilyang - git push origin develop
root@lilyang - Counting objects: 3, done.
Writing objects: 100% (3/3), 200 bytes | 200.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/lily/myproject.git
 * [new branch]      develop -> develop
```

```
root@lilyang - git pull origin main
root@lilyang - Already up to date.
```

```
root@lilyang - git clone https://github.com/lily/myproject.git
root@lilyang - Cloning into 'myproject'...
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (8/8), done.
Receiving objects: 100% (10/10), 2.50 KiB | 2.50 MiB/s, done.
```

```
root@lilyang - git diff
root@lilyang - (Shows differences between working directory and index)
```

```
root@lilyang - git stash
root@lilyang - Saved working directory and index state WIP on develop: abc1234 Initial commit
```

```
root@lilyang - git stash list
root@lilyang - stash@{0}: WIP on develop: abc1234 Initial commit
```

```
root@lilyang - git stash pop
root@lilyang - On branch develop
Changes not staged for commit:
    modified:   README.md
```

```
root@lilyang - git tag v1.0
root@lilyang - (No output)
```

```
root@lilyang - git show v1.0
root@lilyang - commit abc1234 (tag: v1.0)
Author: Lily Yang <lily@example.com>
Date:   Sat Nov 16 12:00:00 2025 +0630
    Initial commit
```

```
root@lilyang - git remote -v
root@lilyang - origin  https://github.com/lily/myproject.git (fetch)
origin  https://github.com/lily/myproject.git (push)
```

```
root@lilyang - git branch -a
root@lilyang - * main
  develop
  remotes/origin/main
  remotes/origin/develop
```

```
root@lilyang - git branch -d feature/login
root@lilyang - Deleted branch feature/login (was abc1234).
```

```
root@lilyang - git reset --hard HEAD~1
root@lilyang - HEAD is now at abc1234 Initial commit
```

```
root@lilyang - git revert abc1234
root@lilyang - [main 123abcd] Revert "Initial commit"
```

```
root@lilyang - git fetch origin
root@lilyang - From https://github.com/lily/myproject
 * branch            main       -> FETCH_HEAD
```

```
root@lilyang - git fetch --all
root@lilyang - Fetching origin
```

```
root@lilyang - git remote remove origin
root@lilyang - (No output)
```

```
root@lilyang - git config --global user.name "Lily Yang"
root@lilyang - (No output)
```

```
root@lilyang - git config --global user.email "lily@example.com"
root@lilyang - (No output)
```

```
root@lilyang - git config --list
root@lilyang - user.name=Lily Yang
user.email=lily@example.com
core.repositoryformatversion=0
core.filemode=true
core.bare=false
```

```
root@lilyang - git clean -f
root@lilyang - (Removes untracked files)
```

```
root@lilyang - git mv oldname.txt newname.txt
root@lilyang - (No output)
```

```
root@lilyang - git rm file.txt
root@lilyang - rm 'file.txt'
```

```
root@lilyang - git blame README.md
root@lilyang - abc1234 (Lily Yang 2025-11-16 12:00:00) Initial commit
```

```
root@lilyang - git shortlog
root@lilyang - Lily Yang (1):
      Initial commit
```

```
root@lilyang - git reflog
root@lilyang - abc1234 HEAD@{0}: commit (initial): Initial commit
```

```
root@lilyang - git cherry-pick abc1234
root@lilyang - [main 456def] Picked commit abc1234
```

```
root@lilyang - git show HEAD
root@lilyang - commit 456def (HEAD -> main)
Author: Lily Yang <lily@example.com>
Date:   Sat Nov 16 12:10:00 2025 +0630
    Picked commit abc1234
```

```
root@lilyang - git ls-files
root@lilyang - README.md
file1.txt
file2.txt
```

```
root@lilyang - git archive -o project.zip HEAD
root@lilyang - (Creates project.zip with the current branch content)
```

```
root@lilyang - git bisect start
root@lilyang - (No output)
```

```
root@lilyang - git bisect good abc1234
root@lilyang - (No output)
```

```
root@lilyang - git bisect bad def5678
root@lilyang - (No output)
```

```
root@lilyang - git bisect reset
root@lilyang - (No output)
```

---

```
root@lilyang - git log --oneline
root@lilyang - abc1234 Initial commit
456def Picked commit abc1234
```

```
root@lilyang - git log --graph --oneline --all
root@lilyang - * 456def Picked commit abc1234
| * abc1234 Initial commit
```

```
root@lilyang - git log --stat
root@lilyang - commit abc1234
Author: Lily Yang <lily@example.com>
Date:   Sat Nov 16 12:00:00 2025 +0630
 README.md | 10 ++++++++++
 1 file changed, 10 insertions(+)
```

```
root@lilyang - git diff --staged
root@lilyang - (Shows staged changes ready for commit)
```

```
root@lilyang - git diff HEAD
root@lilyang - (Shows all changes since last commit)
```

```
root@lilyang - git checkout HEAD -- file.txt
root@lilyang - (Reverts file.txt to last committed state)
```

```
root@lilyang - git remote show origin
root@lilyang - * remote origin
  Fetch URL: https://github.com/lily/myproject.git
  Push  URL: https://github.com/lily/myproject.git
  HEAD branch: main
  Remote branches:
    develop tracked
    main    tracked
```

```
root@lilyang - git push origin --tags
root@lilyang - Total 1 (delta 0), reused 0 (delta 0)
To https://github.com/lily/myproject.git
 * [new tag]         v1.0 -> v1.0
```

```
root@lilyang - git fetch origin --prune
root@lilyang - From https://github.com/lily/myproject
   xxxxxxx..yyyyyyy  main       -> origin/main
```

```
root@lilyang - git config --global core.editor "nano"
root@lilyang - (No output)
```

```
root@lilyang - git config --global merge.tool "meld"
root@lilyang - (No output)
```

```
root@lilyang - git merge --no-ff feature/login
root@lilyang - Merge made by the 'recursive' strategy.
 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

```
root@lilyang - git merge --abort
root@lilyang - (Merge aborted, returned to pre-merge state)
```

```
root@lilyang - git rebase main
root@lilyang - First, rewinding head to replay your work on top of it...
Applying: Added new login feature
```

```
root@lilyang - git rebase --abort
root@lilyang - (Aborted rebase, restored original branch)
```

```
root@lilyang - git checkout -f
root@lilyang - (Discard all local changes)
```

```
root@lilyang - git revert -n abc1234
root@lilyang - (Reverts commit without committing)
```

```
root@lilyang - git reflog expire --expire=now --all
root@lilyang - (No output)
```

```
root@lilyang - git gc --prune=now
root@lilyang - (Optimizes repository, removes unreachable objects)
```

```
root@lilyang - git show-branch
root@lilyang - [main] Initial commit
 [develop] Picked commit abc1234
```

```
root@lilyang - git describe --tags
root@lilyang - v1.0
```

```
root@lilyang - git ls-remote
root@lilyang - abc1234        HEAD
def5678        refs/heads/main
```

```
root@lilyang - git blame -L 1,10 README.md
root@lilyang - abc1234 (Lily Yang 2025-11-16 12:00:00) Initial commit
...
```

```
root@lilyang - git clean -fd
root@lilyang - (Removed untracked files and directories)
```

```
root@lilyang - git mv file1.txt file2.txt
root@lilyang - (No output)
```

```
root@lilyang - git rm --cached file.txt
root@lilyang - rm 'file.txt'
```

```
root@lilyang - git commit --amend
root@lilyang - [main abc1234] Initial commit (amended)
```

```
root@lilyang - git rebase -i HEAD~3
root@lilyang - (Opens interactive rebase for last 3 commits)
```

```
root@lilyang - git stash save "WIP: added login"
root@lilyang - Saved working directory and index state WIP on develop: abc1234 Initial commit
```

```
root@lilyang - git stash apply stash@{0}
root@lilyang - (Applies stash without removing it)
```

```
root@lilyang - git stash drop stash@{0}
root@lilyang - Dropped stash@{0} (WIP: added login)
```

```
root@lilyang - git log --pretty=oneline --abbrev-commit
root@lilyang - abc1234 Initial commit
456def Picked commit abc1234
```

```
root@lilyang - git log --pretty=format:"%h - %an, %ar : %s"
root@lilyang - abc1234 - Lily Yang, 1 hour ago : Initial commit
456def - Lily Yang, 30 mins ago : Picked commit abc1234
```

```
root@lilyang - git reflog show main
root@lilyang - abc1234 HEAD@{0}: commit (initial): Initial commit
456def HEAD@{1}: commit: Picked commit abc1234
```

```
root@lilyang - git submodule add https://github.com/other/repo.git submodule_dir
root@lilyang - Cloning into 'submodule_dir'...
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (8/8), done.
Receiving objects: 100% (10/10), done.
```

```
root@lilyang - git submodule update --init --recursive
root@lilyang - (Initializes and updates submodules)
```

```
root@lilyang - git fsck
root@lilyang - (Checks repository for errors, no output if clean)
```

```
root@lilyang - git verify-commit abc1234
root@lilyang - (Verifies the GPG signature of the commit)
```

```
root@lilyang - git config --global alias.co checkout
root@lilyang - (No output)
```

```
root@lilyang - git co develop
root@lilyang - Switched to branch 'develop'
```

```
root@lilyang - git config --global alias.br "branch -a"
root@lilyang - (No output)
```

```
root@lilyang - git br
root@lilyang - * main
  develop
  remotes/origin/main
  remotes/origin/develop
```

---

```
root@lilyang - git show HEAD~1
root@lilyang - commit abc1234
Author: Lily Yang <lily@example.com>
Date:   Sat Nov 16 12:00:00 2025 +0630
    Initial commit
```

```
root@lilyang - git diff --name-only
root@lilyang - README.md
file1.txt
file2.txt
```

```
root@lilyang - git diff --cached
root@lilyang - (Shows staged changes ready for commit)
```

```
root@lilyang - git log --graph --decorate
root@lilyang - * commit 456def (HEAD -> main)
| * commit abc1234 (develop)
```

```
root@lilyang - git reset HEAD file.txt
root@lilyang - (Unstages file.txt)
```

```
root@lilyang - git checkout -- file.txt
root@lilyang - (Discards changes in file.txt)
```

```
root@lilyang - git reflog expire --expire-unreachable=now --all
root@lilyang - (No output)
```

```
root@lilyang - git gc --aggressive
root@lilyang - (Optimizes repository aggressively)
```

```
root@lilyang - git prune
root@lilyang - (Removes unreachable objects)
```

```
root@lilyang - git bundle create repo.bundle --all
root@lilyang - (Creates bundle file of entire repository)
```

```
root@lilyang - git bundle verify repo.bundle
root@lilyang - The bundle records a total of 2 refs.
```

```
root@lilyang - git ls-tree HEAD
root@lilyang - 100644 blob abc1234 README.md
100644 blob def5678 file1.txt
```

```
root@lilyang - git show HEAD:file1.txt
root@lilyang - (Shows content of file1.txt in HEAD)
```

```
root@lilyang - git cat-file -p abc1234
root@lilyang - (Shows commit object details for abc1234)
```

```
root@lilyang - git rev-parse HEAD
root@lilyang - abc1234
```

```
root@lilyang - git merge --squash feature/login
root@lilyang - Squash commit -- not yet committed
```

```
root@lilyang - git commit -m "Squashed feature/login"
root@lilyang - [main 789ghi] Squashed feature/login
```

```
root@lilyang - git reflog show develop
root@lilyang - 456def HEAD@{0}: commit: Picked commit abc1234
abc1234 HEAD@{1}: checkout: moving from main to develop
```

```
root@lilyang - git rev-list HEAD
root@lilyang - abc1234
456def
```

```
root@lilyang - git shortlog -s -n
root@lilyang - 2  Lily Yang
```

```
root@lilyang - git log --author="Lily Yang"
root@lilyang - commit abc1234
Author: Lily Yang <lily@example.com>
Date:   Sat Nov 16 12:00:00 2025 +0630
    Initial commit
```

```
root@lilyang - git log --grep="login"
root@lilyang - commit 456def
Author: Lily Yang <lily@example.com>
Date:   Sat Nov 16 12:10:00 2025 +0630
    Added login feature
```

```
root@lilyang - git archive --format=tar HEAD | tar -tvf -
root@lilyang - -rw-r--r-- lily/lily  1024 2025-11-16 12:00 README.md
-rw-r--r-- lily/lily  512 2025-11-16 12:05 file1.txt
```

```
root@lilyang - git worktree add ../myproject-test develop
root@lilyang - Preparing worktree (checking out 'develop')
```

```
root@lilyang - git worktree list
root@lilyang - /home/lily/myproject  HEAD
/home/lily/myproject-test  develop
```

```
root@lilyang - git reflog expire --expire=now --all
root@lilyang - (No output)
```

```
root@lilyang - git fsck --full
root@lilyang - (Checks repository for consistency, no output if clean)
```

```
root@lilyang - git verify-tag v1.0
root@lilyang - (Verifies tag signature)
```

```
root@lilyang - git config --global credential.helper store
root@lilyang - (No output)
```

```
root@lilyang - git credential fill
root@lilyang - protocol=https
host=github.com
username=lily
password=******
```

```
root@lilyang - git bundle create mybundle.bundle HEAD develop
root@lilyang - (Creates a bundle containing HEAD and develop)
```

```
root@lilyang - git bisect start
root@lilyang - (Starts bisect session)
```

```
root@lilyang - git bisect good abc1234
root@lilyang - (Marks commit abc1234 as good)
```

```
root@lilyang - git bisect bad 456def
root@lilyang - (Marks commit 456def as bad)
```

```
root@lilyang - git bisect reset
root@lilyang - (Resets bisect session)
```

```
root@lilyang - git format-patch -1 HEAD
root@lilyang - 0001-Picked-commit-abc1234.patch
```

```
root@lilyang - git am 0001-Picked-commit-abc1234.patch
root@lilyang - Applying: Picked commit abc1234
```

```
root@lilyang - git bundle unbundle repo.bundle
root@lilyang - Unbundled 2 commits
```

```
root@lilyang - git reflog expire --expire=now --all
root@lilyang - (No output)
```

```
root@lilyang - git gc --prune=now
root@lilyang - (Optimizes repository, removes unreachable objects)
```

```
root@lilyang - git reflog show --all
root@lilyang - abc1234 HEAD@{0}: commit (initial): Initial commit
456def HEAD@{1}: commit: Picked commit abc1234
```

```
root@lilyang - git log --patch
root@lilyang - commit abc1234
Author: Lily Yang <lily@example.com>
Date:   Sat Nov 16 12:00:00 2025 +0630
diff --git a/README.md b/README.md
new file mode 100644
index 0000000..abc1234
--- /dev/null
+++ b/README.md
@@ -0,0 +1,10 @@
+Initial commit
```

```
root@lilyang - git show-ref
root@lilyang - abc1234 refs/heads/main
456def refs/heads/develop
```

```
root@lilyang - git name-rev abc1234
root@lilyang - abc1234 main
```

---

```
root@lilyang - git reflog show develop
root@lilyang - 456def HEAD@{0}: commit: Picked commit abc1234
abc1234 HEAD@{1}: checkout: moving from main to develop
```

```
root@lilyang - git log --reverse
root@lilyang - commit abc1234
Author: Lily Yang <lily@example.com>
Date:   Sat Nov 16 12:00:00 2025 +0630
    Initial commit
```

```
root@lilyang - git log --since="2 days ago"
root@lilyang - commit 456def
Author: Lily Yang <lily@example.com>
Date:   Sat Nov 14 12:00:00 2025 +0630
    Added login feature
```

```
root@lilyang - git log --until="yesterday"
root@lilyang - commit abc1234
Author: Lily Yang <lily@example.com>
Date:   Fri Nov 15 12:00:00 2025 +0630
    Initial commit
```

```
root@lilyang - git log --stat --summary
root@lilyang - commit 456def
README.md | 2 +-
1 file changed, 1 insertion(+), 1 deletion(-)
```

```
root@lilyang - git log -p -2
root@lilyang - commit 456def
diff --git a/README.md b/README.md
index abc1234..def5678 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,2 @@
 Initial commit
+Added login feature
```

```
root@lilyang - git diff HEAD~1..HEAD
root@lilyang - (Shows diff between last two commits)
```

```
root@lilyang - git diff branch1..branch2
root@lilyang - (Shows differences between branch1 and branch2)
```

```
root@lilyang - git checkout -b hotfix v1.0
root@lilyang - Switched to a new branch 'hotfix'
```

```
root@lilyang - git cherry -v develop main
root@lilyang - + abc1234 Added login feature
```

```
root@lilyang - git cherry-pick abc1234
root@lilyang - [hotfix 789ghi] Picked commit abc1234
```

```
root@lilyang - git tag -a v1.1 -m "Version 1.1 release"
root@lilyang - (No output)
```

```
root@lilyang - git push origin v1.1
root@lilyang - Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/lily/myproject.git
 * [new tag]         v1.1 -> v1.1
```

```
root@lilyang - git push --delete origin v1.1
root@lilyang - To https://github.com/lily/myproject.git
 - [deleted]         v1.1
```

```
root@lilyang - git branch -m main master
root@lilyang - (Renamed branch 'main' to 'master')
```

```
root@lilyang - git reset --soft HEAD~1
root@lilyang - (Moves HEAD back one commit but keeps changes staged)
```

```
root@lilyang - git reset --mixed HEAD~1
root@lilyang - (Moves HEAD back one commit and unstages changes)
```

```
root@lilyang - git reflog expire --expire-unreachable=now --all
root@lilyang - (No output)
```

```
root@lilyang - git cherry-pick --abort
root@lilyang - (Aborts ongoing cherry-pick)
```

```
root@lilyang - git log --left-right --graph --cherry-pick develop...main
root@lilyang - * 456def Picked commit abc1234
<  abc1234 Initial commit
```

```
root@lilyang - git blame -C -C README.md
root@lilyang - abc1234 (Lily Yang 2025-11-16 12:00:00) Initial commit
```

```
root@lilyang - git branch --contains abc1234
root@lilyang - main
develop
hotfix
```

```
root@lilyang - git diff --stat HEAD~2 HEAD
root@lilyang - README.md | 2 +-
1 file changed, 1 insertion(+), 1 deletion(-)
```

```
root@lilyang - git log --pretty=format:"%h %s" --graph
root@lilyang - * 456def Picked commit abc1234
* abc1234 Initial commit
```

```
root@lilyang - git diff --name-status HEAD~2 HEAD
root@lilyang - M README.md
```

```
root@lilyang - git revert -m 1 abc1234
root@lilyang - [main 123abc] Revert "Initial commit"
```

```
root@lilyang - git reset --hard ORIG_HEAD
root@lilyang - (Resets to original HEAD before last operation)
```

```
root@lilyang - git fsck --full --strict
root@lilyang - (Checks repository integrity strictly)
```

```
root@lilyang - git verify-commit HEAD
root@lilyang - (Verifies GPG signature of HEAD commit)
```

```
root@lilyang - git verify-tag v1.0
root@lilyang - (Verifies GPG signature of tag v1.0)
```

```
root@lilyang - git remote set-url origin https://github.com/lily/newproject.git
root@lilyang - (No output)
```

```
root@lilyang - git reflog delete HEAD@{1}
root@lilyang - (Deletes the specific reflog entry)
```

```
root@lilyang - git stash branch new-feature
root@lilyang - Switched to a new branch 'new-feature'
```

```
root@lilyang - git log --pretty=oneline --abbrev-commit --all
root@lilyang - abc1234 Initial commit
456def Picked commit abc1234
789ghi Squashed feature/login
```

```
root@lilyang - git tag -l "v1.*"
root@lilyang - v1.0
v1.1
```

```
root@lilyang - git reflog expire --expire=now --all
root@lilyang - (No output)
```

```
root@lilyang - git gc --aggressive --prune=now
root@lilyang - (Optimizes and prunes unreachable objects aggressively)
```

---

