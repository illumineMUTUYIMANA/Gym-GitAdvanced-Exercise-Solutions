# Git Advanced excersice solutions
## Part1
### 1: Missing File Fix

User@Illumin▒epc MINGW64 /d
$ git clone https://github.com/illumineMUTUYIMANA/Gym-GitAdvanced-Exercise-Solutions.git
Cloning into 'Gym-GitAdvanced-Exercise-Solutions'...
warning: You appear to have cloned an empty repository.

User@Illumin▒epc MINGW64 /d
$ ^C

User@Illumin▒epc MINGW64 /d
$ cd Gym-GitAdvanced-Exercise-Solutions

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ touch test{1..4}.md
git add test1.md && git commit -m "chore: Create initial file"
git add test2.md && git commit -m "chore: Create another file"
git add test3.md && git commit -m "chore: Create third and fourth files"
[main (root-commit) 2079488] chore: Create initial file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
[main fdd3d77] chore: Create another file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
[main 8b0af11] chore: Create third and fourth files
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git status
On branch main
Your branch is based on 'origin/main', but the upstream is gone.
  (use "git branch --unset-upstream" to fixup)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git log
commit 8b0af11b794507699ef2c8df263bbe29cb2720b9 (HEAD -> main)
Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
Date:   Wed Jun 10 13:41:02 2026 +0200

    chore: Create third and fourth files

commit fdd3d77cf2c6262b4bf47b3f6b9d18182990d14b
Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
Date:   Wed Jun 10 13:41:02 2026 +0200

    chore: Create another file

commit 2079488823a29ee3eb7c1b2b0c67dd0e399afac9
Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
Date:   Wed Jun 10 13:41:01 2026 +0200

    chore: Create initial file

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ ^C

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git branch --unset-upstream

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git add test4.md

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   test4.md


User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git commit --amend -m "include test4.md"
[main 8d912aa] include test4.md
 Date: Wed Jun 10 13:41:02 2026 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git status
On branch main
nothing to commit, working tree clean

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-Exercise-Solutions (main)
$ git log
commit 8d912aa8662633629ca44ad58a026d68f0489049 (HEAD -> main)
Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
Date:   Wed Jun 10 13:41:02 2026 +0200

    include test4.md

commit fdd3d77cf2c6262b4bf47b3f6b9d18182990d14b
Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
Date:   Wed Jun 10 13:41:02 2026 +0200

    chore: Create another file

commit 2079488823a29ee3eb7c1b2b0c67dd0e399afac9
Author: Illuminee mutuyimana <mutuyiillumine2@gmail.com>
Date:   Wed Jun 10 13:41:01 2026 +0200

    chore: Create initial file

### 2: Editing Commit History

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git reset --hard ORIG_HEAD
HEAD is now at 8d912aa include test4.md

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git rebase -i HEAD~2
[detached HEAD e4391e0] Create second file
 Date: Wed Jun 10 13:41:02 2026 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
2ee8e15 (HEAD -> main) include test4.md
e4391e0 Create second file
2079488 chore: Create initial file

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)

### 3: Keeping History Tidy - Squashing Commits

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git rebase -i HEAD~2
error: could not read file '.git/rebase-merge/git-rebase-todo': No such file or directory

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git rebase -i HEAD~3
fatal: invalid upstream 'HEAD~3'

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
2ee8e15 (HEAD -> main) include test4.md
e4391e0 Create second file
2079488 chore: Create initial file

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git rebase -i --root
[detached HEAD 6777447] chore: Create initial file
 Date: Wed Jun 10 13:41:01 2026 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$ git log --oneline
efa7e59 (HEAD -> main) include test4.md
6777447 chore: Create initial file

User@Illumin▒epc MINGW64 /d/Gym-GitAdvanced-repo (main)
$

### 4: 
