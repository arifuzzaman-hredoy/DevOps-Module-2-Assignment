# Nanu's Recipe Book — Git Assignment Report

## 1. Project Overview

This project demonstrates Git version control through Nanu's Recipe Book. I practiced repository initialization, staging, committing, branching, merging, conflict resolution, remote repositories, cloning, fetching, pulling, stashing, moving files, deleting files, and inspecting commit history.

GitHub Repository: https://github.com/arifuzzaman-hredoy/DevOps-Module-2-Assignment

## 2. Chapter 1: Git Basics

I configured my Git identity and initialized the `nanur-khata` repository.

Commands practiced:

* `git config --global user.name`
* `git config --global user.email`
* `git init`
* `git status`
* `git add`
* `git diff`
* `git diff --staged`
* `git commit`
* `git reset`

I created the Bhapa Pitha recipe and updated the jaggery quantity from 2 cups to 1.5 cups.

I also staged `bazar-list.txt` and used `git reset bazar-list.txt` to unstage it without deleting the file.

## 3. Chapter 2: .gitignore

I created a `.gitignore` file containing:

```
secret-masala.txt
*.tmp
draft/
```

These rules ignore the secret recipe file, temporary files, and the draft directory.

I verified the ignore rules with Git status and ignore-related checks.

The secret recipe was kept out of version control.

## 4. Chapter 3: Branching and Merging

I created the `eid-special` branch and added Biryani and Shemai recipes in separate commits.

I merged the branch into `main`.

I also practiced a merge conflict using `conflict-recipe.md`. Two branches changed the sugar quantity differently. Git reported a conflict, and I resolved it by keeping 4 tablespoons of sugar.

After resolving the conflict, I staged and committed the corrected file.

## 5. Chapter 4: Remote Repositories

I connected my local repository to GitHub using a remote named `origin`.

I pushed the `main` branch to GitHub and cloned the repository into a separate directory for Mitu.

Mitu added the Chittagong Mezban recipe and pushed it to the remote repository. A later recipe change was also pushed from the clone.

In the original repository, I used `git fetch` and `git merge` to integrate remote changes. I also practiced `git pull`.

### Fetch + Merge vs Pull

* `git fetch` downloads remote updates without merging them into the current branch.
* `git merge` integrates the selected branch into the current branch.
* `git pull` fetches remote changes and then integrates them into the current branch.

## 6. Chapter 5: Stash, File Organization, and History

### Stashing unfinished work

I started an unfinished `halua.md` recipe and saved it using:

```
git stash push -m "Save unfinished halua recipe"
```

I improved the Biryani serving instructions, committed the change, and restored the unfinished Halua work using:

```
git stash pop
```

I then completed and committed the Halua recipe.

### Organizing recipes

I created category directories and used `git mv` to organize the recipes:

* `recipes/rice-dishes/biryani.md`
* `recipes/sweets/shemai.md`
* `recipes/sweets/halua.md`
* `recipes/traditional/bhapa-pitha.md`
* `recipes/traditional/chittagong-mezban.md`
* `recipes/traditional/sylheti-shakora.md`

I inspected rename detection using:

```
git log --stat -M
```

### Deleting an outdated recipe

I created and committed `old-recipe.md`, then removed it using:

```
git rm old-recipe.md
```

I committed the deletion separately so the history records both the file's creation and removal.

### Inspecting a commit

I used:

```
git show 5c9f5ad
```

This displayed the Biryani improvement commit and its recorded changes.

### Practicing reset --hard safely

I created a separate branch named `reset-test` and ran:

```
git reset --hard 136cb87
```

The test branch moved back to the recipe organization commit. The later draft creation and deletion commits no longer appeared in the test branch's current history.

I switched back to `main` and verified that those commits remained in the main branch.

### Why reset --hard and rebase can be dangerous

`git reset --hard` can move a branch backwards and discard uncommitted tracked-file changes. Commits removed from a branch's current history may become difficult to find if no reference remains.

`git rebase` rewrites commit history and may create new commit hashes. Rewriting a shared branch can disrupt collaborators who based their work on the old history.

These operations require particular care on shared branches.

## 7. Important Git Commands Practiced

```
git init
git status
git add
git diff
git diff --staged
git commit
git reset
git branch
git checkout
git switch
git merge
git remote add origin
git push
git clone
git fetch
git pull
git stash
git stash pop
git mv
git rm
git log --oneline
git log --stat -M
git show
git reset --hard
```

## 8. Final Verification

Before submission, I will verify:

* The repository is pushed to GitHub.
* The working tree is clean.
* The required branches are present.
* The commit history is visible.
* `.gitignore` excludes secret and temporary files.
* This report is committed to the repository.

Final history command:

```
git log --oneline --graph --all
```

## 9. Screenshots

Add screenshots showing:

1. Git configuration and repository initialization.
2. The `.gitignore` rules and verification.
3. Branch creation and merging.
4. Merge conflict and its resolution.
5. Remote repository operations.
6. Stash, recipe organization, and file deletion.
7. The `reset-test` experiment.
8. Final Git history and GitHub repository.

## 10. Conclusion

This project helped me practice Git version control in a realistic recipe-book scenario. I learned how to track changes, collaborate through remote repositories, manage branches, resolve conflicts, save unfinished work, organize files, and inspect or carefully test changes to commit history.

