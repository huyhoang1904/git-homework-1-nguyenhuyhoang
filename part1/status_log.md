On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	./

nothing added to commit but untracked files present (use "git add" to track)

## After staging notes.txt and todo.txt
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   notes.txt
	new file:   todo.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	draft.md
	status_log.md


## git diff (unstaged changes to notes.txt)
diff --git a/part1/notes.txt b/part1/notes.txt
index e69de29..136fbf1 100644
--- a/part1/notes.txt
+++ b/part1/notes.txt
@@ -0,0 +1,3 @@
+Hello world
+I am a student in PTIT
+Nice to meet you!

## git diff --staged (after staging notes.txt)
diff --git a/part1/notes.txt b/part1/notes.txt
index e69de29..136fbf1 100644
--- a/part1/notes.txt
+++ b/part1/notes.txt
@@ -0,0 +1,3 @@
+Hello world
+I am a student in PTIT
+Nice to meet you!
## Why 'git commit -a' works here
The -a flag automatically stages all changes to files that are already
tracked by Git (i.e., files that have been commit before), before 
creating the commit. Sinces notes.txt was already tracked (committed in
step 4), -a picked up its modification automatically without needing 
a separate 'git add'.
However, -a doesn't work for new/untracked files. If draft.md were 
modified, -a would ignore it because Git has never tracked draft.md 
before - new files must always be explicitly staged with 'git add'
at least once before Git can track their changes.
## Different between git fetch and git pull
'git fetch origin' downloads new commits, branches, and data from the
remote repository (GitHub) into the local remote-tracking branch
(origin/main), but it doesn't change any files in the working directory
or merge anything into the current branch. It only lets you see what 
change on the remote before deciding what to do.
'git pull origin main' is essentially 'git fetch' followed by 
'git merge origin/main' - it downloads the new commits and immediately 
merges them into the current local branch, updating the actual files
in the working directory.
