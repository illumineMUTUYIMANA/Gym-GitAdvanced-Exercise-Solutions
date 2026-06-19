# Git Advanced excersice solutions
## Part1
### 1: Missing File Fix
```bash
User@Illumin▒epc MINGW64 /d
$ git clone https://github.com/illumineMUTUYIMANA/Gym-GitAdvanced-Exercise-Solutions.git

User@Illumin▒epc MINGW64 /d
$ cd Gym-GitAdvanced-Exercise-Solutions

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ touch test{1..4}.md
git add test1.md && git commit -m "chore: Create initial file"
git add test2.md && git commit -m "chore: Create another file"
git add test3.md && git commit -m "chore: Create third and fourth files"

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git status
On branch main


User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git log


User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git branch --unset-upstream

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git status
On branch main

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git add test4.md

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git status

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git commit --amend -m "include test4.md"

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git status


User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git log
```

### 2: Editing Commit History

```bash

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git reset --hard ORIG_HEAD
HEAD is now at 8d912aa include test4.md

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git rebase -i HEAD~2

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
2ee8e15 (HEAD -> main) include test4.md
e4391e0 Create second file
2079488 chore: Create initial file

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)

```

### 3: Keeping History Tidy - Squashing Commits

```bash

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
2ee8e15 (HEAD -> main) include test4.md
e4391e0 Create second file
2079488 chore: Create initial file

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git rebase -i --root

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
efa7e59 (HEAD -> main) include test4.md
6777447 chore: Create initial file

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$
```

### 4: Splitting a Commit

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git reset HEAD~1

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test3.md
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git add test3.md

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit -m "Create Third File"

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git add test4.md

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit -m "Create fourth file"

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git status
On branch main
nothing to commit, working tree clean

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log
```

### 5: Advanced Squashing
```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git reset --soft HEAD~2

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit -m "Create third and fourth files"
[main a8c8aab] Create third and fourth files
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
a8c8aab (HEAD -> main) Create third and fourth files
6777447 chore: Create initial file

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ 
```

### 6: Dropping a Commit

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git add unwanted.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit -m "Unwanted commit"
[main 285253a] Unwanted commit
 1 file changed, 3 insertions(+)
 create mode 100644 unwanted.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
285253a (HEAD -> main) Unwanted commit
a8c8aab Create third and fourth files
6777447 chore: Create initial file

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git rebase -i HEAD~1
Successfully rebased and updated refs/heads/main.                                            

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ 
```

### 7: Reordering Commits
```bash

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git rebase -i HEAD~2
fatal: invalid upstream 'HEAD~2'

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit --allow-empty -m "Temporary Commit A"
git commit --allow-empty -m "Temporary Commit B"
[main 913437a] Temporary Commit A
[main 77716f1] Temporary Commit B

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git rebase -i HEAD~3
Successfully rebased and updated refs/heads/main.                                                        

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
4dbe173 (HEAD -> main) Temporary Commit A
e5a7797 Temporary Commit B
a8c8aab Create third and fourth files
6777447 chore: Create initial file

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ 
```

### 8: Cherry-Picking Commits

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git checkout -b ft/branch
Switched to a new branch 'ft/branch'

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/branch)
$ echo "this is the content of test5.md on branch ft/branch" >touch test5.md

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/branch)
$ echo "this is the content of test5.md on branch ft/branch" > test5.md

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/branch)
$ rm touch

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/branch)
$ ls
test1.md  test2.md  test3.md  test4.md  test5.md

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/branch)
$ git add .
warning: in the working copy of 'test5.md', LF will be replaced by CRLF the next time Git touches it

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/branch)
$ git status
On branch ft/branch
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   test5.md


User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/branch)
$ git commit -m "Implemented test 5"
[ft/branch 7bd1c51] Implemented test 5
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/branch)
$ git log --oneline
7bd1c51 (HEAD -> ft/branch) Implemented test 5
4dbe173 (main) Temporary Commit A
e5a7797 Temporary Commit B
a8c8aab Create third and fourth files
6777447 chore: Create initial file

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/branch)
$ git checkout main
Switched to branch 'main'

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git cherry-pick 7bd1c51
[main 29d7f6e] Implemented test 5
 Date: Mon Jun 15 13:45:29 2026 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ ls
test1.md  test2.md  test3.md  test4.md  test5.md

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
29d7f6e (HEAD -> main) Implemented test 5
4dbe173 Temporary Commit A
e5a7797 Temporary Commit B
a8c8aab Create third and fourth files
6777447 chore: Create initial file

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ 
```

### 9: Visualizing Commit History (Bonus)

```bash

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --graph
* commit 29d7f6ea62428f12a7006f7de27dd0bf9705884a (HEAD -> main)
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:45:29 2026 +0200
| 
|     Implemented test 5
| 
* commit 4dbe173951b081db976623ec37572524a9ef0384
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:26 2026 +0200
:...skipping...
* commit 29d7f6ea62428f12a7006f7de27dd0bf9705884a (HEAD -> main)
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:45:29 2026 +0200
| 
|     Implemented test 5
| 
* commit 4dbe173951b081db976623ec37572524a9ef0384
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:26 2026 +0200
| 
|     Temporary Commit A
| 
* commit e5a7797bd02a11d2b7526733d87823b26e842176
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:27 2026 +0200
:...skipping...
* commit 29d7f6ea62428f12a7006f7de27dd0bf9705884a (HEAD -> main)
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:45:29 2026 +0200
| 
|     Implemented test 5
| 
* commit 4dbe173951b081db976623ec37572524a9ef0384
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:26 2026 +0200
| 
|     Temporary Commit A
| 
* commit e5a7797bd02a11d2b7526733d87823b26e842176
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:27 2026 +0200
| 
:...skipping...
* commit 29d7f6ea62428f12a7006f7de27dd0bf9705884a (HEAD -> main)
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:45:29 2026 +0200
| 
|     Implemented test 5
| 
* commit 4dbe173951b081db976623ec37572524a9ef0384
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:26 2026 +0200
| 
|     Temporary Commit A
| 
* commit e5a7797bd02a11d2b7526733d87823b26e842176
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:27 2026 +0200
| 
|     Temporary Commit B
:...skipping...
* commit 29d7f6ea62428f12a7006f7de27dd0bf9705884a (HEAD -> main)
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:45:29 2026 +0200
| 
|     Implemented test 5
| 
* commit 4dbe173951b081db976623ec37572524a9ef0384
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:26 2026 +0200
| 
|     Temporary Commit A
| 
* commit e5a7797bd02a11d2b7526733d87823b26e842176
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:27 2026 +0200
| 
|     Temporary Commit B
| 
:...skipping...
* commit 29d7f6ea62428f12a7006f7de27dd0bf9705884a (HEAD -> main)
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:45:29 2026 +0200
| 
|     Implemented test 5
| 
* commit 4dbe173951b081db976623ec37572524a9ef0384
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:26 2026 +0200
| 
|     Temporary Commit A
| 
* commit e5a7797bd02a11d2b7526733d87823b26e842176
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:27 2026 +0200
| 
|     Temporary Commit B
| 
* commit a8c8aaba694c84c196878082bac16f7d7b2427d5
:...skipping...
* commit 29d7f6ea62428f12a7006f7de27dd0bf9705884a (HEAD -> main)
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:45:29 2026 +0200
| 
|     Implemented test 5
| 
* commit 4dbe173951b081db976623ec37572524a9ef0384
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:26 2026 +0200
| 
|     Temporary Commit A
| 
* commit e5a7797bd02a11d2b7526733d87823b26e842176
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:27 2026 +0200
| 
|     Temporary Commit B
| 
* commit a8c8aaba694c84c196878082bac16f7d7b2427d5
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
:...skipping...
* commit 29d7f6ea62428f12a7006f7de27dd0bf9705884a (HEAD -> main)
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:45:29 2026 +0200
| 
|     Implemented test 5
| 
* commit 4dbe173951b081db976623ec37572524a9ef0384
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:26 2026 +0200
| 
|     Temporary Commit A
| 
* commit e5a7797bd02a11d2b7526733d87823b26e842176
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:27 2026 +0200
| 
|     Temporary Commit B
| 
* commit a8c8aaba694c84c196878082bac16f7d7b2427d5
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Sat Jun 13 22:54:32 2026 +0200
:...skipping...
* commit 29d7f6ea62428f12a7006f7de27dd0bf9705884a (HEAD -> main)
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:45:29 2026 +0200
| 
|     Implemented test 5
| 
* commit 4dbe173951b081db976623ec37572524a9ef0384
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:26 2026 +0200
| 
|     Temporary Commit A
| 
* commit e5a7797bd02a11d2b7526733d87823b26e842176
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Mon Jun 15 13:14:27 2026 +0200
| 
|     Temporary Commit B
| 
* commit a8c8aaba694c84c196878082bac16f7d7b2427d5
| Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
| Date:   Sat Jun 13 22:54:32 2026 +0200
| 
:
```

### 10: Understanding Reflogs (Bonus)

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git reflog
29d7f6e (HEAD -> main) HEAD@{0}: cherry-pick: Implemented test 5
4dbe173 HEAD@{1}: checkout: moving from ft/branch to main
7bd1c51 (ft/branch) HEAD@{2}: commit: Implemented test 5
4dbe173 HEAD@{3}: checkout: moving from main to ft/branch
4dbe173 HEAD@{4}: rebase (finish): returning to refs/heads/main
4dbe173 HEAD@{5}: rebase (pick): Temporary Commit A
e5a7797 HEAD@{6}: rebase (pick): Temporary Commit B
a8c8aab HEAD@{7}: rebase (start): checkout HEAD~3
77716f1 HEAD@{8}: commit: Temporary Commit B
913437a HEAD@{9}: commit: Temporary Commit A
a8c8aab HEAD@{10}: rebase (finish): returning to refs/heads/main
a8c8aab HEAD@{11}: rebase (start): checkout HEAD~1
285253a HEAD@{12}: commit: Unwanted commit
a8c8aab HEAD@{13}: commit: Create third and fourth files
6777447 HEAD@{14}: reset: moving to HEAD~2
010bf51 HEAD@{15}: rebase (abort): returning to refs/heads/main
59fc240 HEAD@{16}: rebase (start): checkout HEAD~2
010bf51 HEAD@{17}: commit: Create fourth file
59fc240 HEAD@{18}: commit: Create Third File
6777447 HEAD@{19}: reset: moving to HEAD~1
efa7e59 HEAD@{20}: rebase (finish): returning to refs/heads/main
efa7e59 HEAD@{21}: rebase (pick): include test4.md
:

```

## part2

### 2: Feature Branch Creation

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'

```

### 2: Working on the Feature Branch
```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/new-feature)
$ echo "feature branch ha this file of feature test for the purpose of learning" > feature.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/new-feature)
$ git add .
warning: in the working copy of 'feature.txt', LF will be replaced by CRLF the next time Git touches it

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/new-feature)
$ git commit -m "Implemented core functionality for new feature"
[ft/new-feature 9730194] Implemented core functionality for new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt


```

### 3: Switching Back and Making More Changes

```bash

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/new-feature)
$ git checkout main
Switched to branch 'main'

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ echo "Hi, I am Illuminee I working on this project of Git advanced" > readme.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git add .
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit -m "Updated project readme"
[main 4211728] Updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt

```

### 4: Local vs. Remote Branches

```bash
git push -u origin <branch-name>
git pull branch-name
git fetch --all

```

### 5: Branch Deletion
```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git branch --merged
* main

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git merge ft/new-feature
Merge made by the 'ort' strategy.
 feature.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git branch --merged
  ft/new-feature
* main

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git branch -d ft/new-feature
Deleted branch ft/new-feature (was 9730194).
```
### 6: Creating a Branch from a Commit

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
91a8cda (HEAD -> main) Merge branch 'ft/new-feature'
4211728 Updated project readme
9730194 Implemented core functionality for new feature
29d7f6e Implemented test 5
4dbe173 Temporary Commit A
e5a7797 Temporary Commit B
a8c8aab Create third and fourth files
6777447 chore: Create initial file

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git checkout -b ft/new-branch-from-commit 9730194
Switched to a new branch 'ft/new-branch-from-commit'

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/new-branch-from-commit)
$ git log --oneline
9730194 (HEAD -> ft/new-branch-from-commit) Implemented core functionality for new feature
29d7f6e Implemented test 5
4dbe173 Temporary Commit A
e5a7797 Temporary Commit B
a8c8aab Create third and fourth files
6777447 chore: Create initial file

```
### 7: Branch Merging
```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/new-branch-from-commit)
$ git checkout main
Switched to branch 'main'

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git merge ft/new-branch-from-commit
Already up to date.

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git branch --merged
  ft/new-branch-from-commit
* main

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ 
```

### 8: Branch Rebasing
```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/new-branch-from-commit)
$ git rebase main
Successfully rebased and updated refs/heads/ft/new-branch-from-commit.                                   

```
### 9: Renaming Branches

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/new-branch-from-commit)
$ git branch -m ft/new-branch-from-commit ft/improved-branch-name

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/improved-branch-name)
$ git branch
  ft/branch
* ft/improved-branch-name
  main

```

### 10: Checking Out Detached HEAD

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
91a8cda (HEAD -> main, ft/improved-branch-name) Merge branch 'ft/new-feature'
4211728 Updated project readme
9730194 Implemented core functionality for new feature
29d7f6e Implemented test 5
4dbe173 Temporary Commit A
e5a7797 Temporary Commit B
a8c8aab Create third and fourth files
6777447 chore: Create initial file

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git checkout 29d7f6e
Note: switching to '29d7f6e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 29d7f6e Implemented test 5

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo ((29d7f6e...))
$ git checkout main
Previous HEAD position was 29d7f6e Implemented test 5
Switched to branch 'main'

```

## part3:  Advanced Workflows (10+ Challenges)

### 1: Stashing Changes
```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git stash -m "practice stash"
Saved working directory and index state On main: practice stash

```

### 2: Retrieving Stashed Changes

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git status
On branch main
nothing to commit, working tree clean

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git stash pop
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (da42080498faf1a954c4c5cc5df8185cec3eb860)

```

### 3: Branch Merging Conflicts (Continued)

```bash

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        testingConflict.txt

no changes added to commit (use "git add" and/or "git commit -a")

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git add testingConflict.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit -m "create and add initial line for conflict file"
[main 5f9d3b0] create and add initial line for conflict file
 1 file changed, 1 insertion(+)
 create mode 100644 testingConflict.txt

 User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git checkout -b ft/conflictTest
Switched to a new branch 'ft/conflictTest'

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/conflictTest)
$ echo "merge Conflict learning in git Adavanced" > testingConflict.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/conflictTest)
$ git add testingConflict.txt
warning: in the working copy of 'testingConflict.txt', LF will be replaced by CRLF the next time Git touches it

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/conflictTest)
$ git commit -m "modified line in feature branch"
[ft/conflictTest 8caaa0e] modified line in feature branch
 1 file changed, 1 insertion(+)
 create mode 100644 testingConflict.txt

 User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/conflictTest)
$ git checkout main
Switched to branch 'main'
M       readme.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ echo "changing again the main initial line in main branch" > testingConflict.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git add testingConflict.txt
warning: in the working copy of 'testingConflict.txt', LF will be replaced by CRLF the next time Git touches it

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit -m "modifying the initial line in main"
[main 491efe9] modifying the initial line in main
 1 file changed, 1 insertion(+), 1 deletion(-)

 User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git merge ft/conflictTest
Auto-merging testingConflict.txt
CONFLICT (add/add): Merge conflict in testingConflict.txt
Automatic merge failed; fix conflicts and then commit the result.

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main|MERGING)
$ git add testingConflict.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main|MERGING)
$ git commit -m "conflict resolved with accept both changes"
[main 5daf8d9] conflict resolved with accept both changes

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$
```

### 4: Resolving Merge Conflicts with a Merge Tool

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        mergToolTest.txt

nothing added to commit but untracked files present (use "git add" to track)

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git add mergToolTest.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit -m "content to test mergetool"
[main 0cec067] content to test mergetool
 1 file changed, 1 insertion(+)
 create mode 100644 mergToolTest.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git checkout ft/conflictTest
Switched to branch 'ft/conflictTest'

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/conflictTest)
$ echo "modifying the content of mergetoll in feature branch" > mergToolTest.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/conflictTest)
$ git add mergToolTest.txt
warning: in the working copy of 'mergToolTest.txt', LF will be replaced by CRLF the next time Git touches it

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/conflictTest)
$ git commit -m "changes in feature branch modifying the main mergetool"
[ft/conflictTest f880f93] changes in feature branch modifying the main mergetool
 1 file changed, 1 insertion(+)
 create mode 100644 mergToolTest.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (ft/conflictTest)
$ git checkout main
Switched to branch 'main'

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ echo "modifying again the content in the main branch" > mergToolTest.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git add mergToolTest.txt
warning: in the working copy of 'mergToolTest.txt', LF will be replaced by CRLF the next time Git touches it

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit -m "in main modify the initial line of mergetool"
[main d05115f] in main modify the initial line of mergetool
 1 file changed, 1 insertion(+), 1 deletion(-)

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git merge ft/conflictTest
Auto-merging mergToolTest.txt
CONFLICT (add/add): Merge conflict in mergToolTest.txt
Automatic merge failed; fix conflicts and then commit the result.

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main|MERGING)
$ git mergetool

This message is displayed because 'merge.tool' is not configured.
See 'git mergetool --tool-help' or 'git help config' for more details.
'git mergetool' will now attempt to use one of the following tools:
opendiff kdiff3 tkdiff xxdiff meld tortoisemerge gvimdiff diffuse diffmerge ecmerge p4merge araxis bc codecompare smerge emerge vimdiff nvimdiff
Merging:
mergToolTest.txt

Normal merge conflict for 'mergToolTest.txt':
  {local}: created file
  {remote}: created file
Hit return to start merge resolution tool (vimdiff): 

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main|MERGING)
$ git config --global merge.tool vscode

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main|MERGING)
$ git config --global mergetool.vscode.cmd 'code --wait "$MERGED"'

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main|MERGING)
$ git config --global mergetool.keepBackup false

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main|MERGING)
$ git mergetool
Merging:
mergToolTest.txt

Normal merge conflict for 'mergToolTest.txt':
  {local}: created file
  {remote}: created file

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main|MERGING)
$ git checkout --ours mergToolTest.txt
Updated 0 paths from the index

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main|MERGING)
$ git add mergToolTest.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main|MERGING)
$ git commit -m "Resolved conflict by keeping ours (main)"
[main 7eb95e0] Resolved conflict by keeping ours (main)

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git checkout ft/conflictTest -- mergToolTest.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git add mergToolTest.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit -m "Restore file content from feature branch"
[main 5ebf121] Restore file content from feature branch
 1 file changed, 1 insertion(+)

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ 
```

### 5: Understanding Detached HEAD State

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo ((a8c8aab...))
$ git log --oneline

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git checkout a8c8aab

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo ((a8c8aab...))
$ git checkout main
```

### 6: Ignoring Files/Directories
```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ touch .gitignore

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ echo "/tmp" >> .gitignore

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ mkdir tmp

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ echo "the secret content to be in ignored" > tmp/secret.txt

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore

nothing added to commit but untracked files present (use "git add" to track)

```

### 7: Working with Tags:
```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git tag v1.0

```

### 8: Listing and Deleting Tags

```bash

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git tag
v1.0

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git tag -d v1.0
Deleted tag 'v1.0' (was 5ebf121)

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git tag

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ 

```

### 9: Pushing Local Work to Remote Repositories

```bash
User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git add .
warning: in the working copy of '.gitignore', LF will be replaced by CRLF the next time Git touches it

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git commit -m "Do git advanced Excercise"
[main 23e5d94] Do git advanced Excercise
 1 file changed, 1 insertion(+)
 create mode 100644 .gitignore

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git push -u origin main
Enumerating objects: 46, done.
Counting objects: 100% (46/46), done.
Delta compression using up to 8 threads
Compressing objects: 100% (41/41), done.
Writing objects: 100% (46/46), 4.11 KiB | 382.00 KiB/s, done.
Total 46 (delta 21), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (21/21), done.                                         
To https://github.com/illumineMUTUYIMANA/Gym-GitAdvanced-repo.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git branch
  ft/branch
  ft/conflictTest
  ft/improved-branch-name
* main

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git push -u origin ft/conflictTest
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'ft/conflictTest' on GitHub by visiting:            
remote:      https://github.com/illumineMUTUYIMANA/Gym-GitAdvanced-repo/pull/new/ft/conflictTest                                                                            
remote: 
To https://github.com/illumineMUTUYIMANA/Gym-GitAdvanced-repo.git
 * [new branch]      ft/conflictTest -> ft/conflictTest
branch 'ft/conflictTest' set up to track 'origin/ft/conflictTest'.

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git push -u origin ft/improved-branch-name
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'ft/improved-branch-name' on GitHub by visiting:    
remote:      https://github.com/illumineMUTUYIMANA/Gym-GitAdvanced-repo/pull/new/ft/improved-branch-name                                                                    
remote: 
To https://github.com/illumineMUTUYIMANA/Gym-GitAdvanced-repo.git
 * [new branch]      ft/improved-branch-name -> ft/improved-branch-name
branch 'ft/improved-branch-name' set up to track 'origin/ft/improved-branch-name'.

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ 

```

### 10: Pulling Changes from Remote Repositories

After editing readme on git hub and commit it.
I went back in vs code and run the following

```bash

User@Illumin□epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git pull origin main
remote: Enumerating objects: 5, done.                                                 
remote: Counting objects: 100% (5/5), done.                                           
remote: Compressing objects: 100% (3/3), done.                                        
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)                 
Unpacking objects: 100% (3/3), 1.07 KiB | 109.00 KiB/s, done.
From https://github.com/illumineMUTUYIMANA/Gym-GitAdvanced-repo
 * branch            main       -> FETCH_HEAD
   23e5d94..16b2bd9  main       -> origin/main
Updating 23e5d94..16b2bd9
Fast-forward
 readme.txt | 6 ++++++
 1 file changed, 6 insertions(+)
 
```

