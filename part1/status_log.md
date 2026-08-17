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
