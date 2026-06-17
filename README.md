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



