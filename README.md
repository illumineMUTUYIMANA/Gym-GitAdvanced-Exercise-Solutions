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




