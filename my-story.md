# Nanu's Recipe Book — My Git Assignment

## 1. Introduction

For this assignment, I worked on a small project called **Nanu's Recipe Book**. I used different Git commands to manage recipes, track changes, and learn how Git works in real projects.

At first, I practiced basic commands. Later, I worked with branches, merge conflicts, GitHub, and some advanced Git commands. I also used a separate clone of my repository to practice how two people can work on the same project.

**GitHub Repository:**
https://github.com/arifuzzaman-hredoy/DevOps-Module-2-Assignment

## 2. Chapter 1: Getting Started with Git

First, I configured my Git username and email. Then I initialized the repository and started working on the recipe files.

```bash
git config --global user.name
git config --global user.email
git init
git status
```

I created `bhapa-pitha.md` and added the ingredients and cooking instructions for Bhapa Pitha.

After that, I changed the amount of date palm jaggery from 2 cups to 1.5 cups. I used `git diff` to see the changes before staging them and `git diff --staged` to check the staged changes.

When everything looked correct, I committed the changes.

I also practiced unstaging a file. I added `bazar-list.txt` to the staging area and then used:

```bash
git reset bazar-list.txt
```

The file remained in my folder, but it was removed from the staging area. This helped me understand that unstaging a file does not mean deleting it.

## 3. Chapter 2: Using .gitignore

Next, I learned how to keep unnecessary or private files out of Git.

I created a `.gitignore` file with these rules:

```gitignore
secret-masala.txt
*.tmp
draft/
```

I created some test files to check whether the rules were working. The secret recipe, temporary files, and files inside the draft directory were ignored.

To verify this, I used:

```bash
git check-ignore -v secret-masala.txt recipe-notes.tmp cooking-time.tmp draft/unfinished-recipe.md
```

I also checked whether those files were tracked by Git.

This part helped me understand why `.gitignore` is useful. It reduces the chance of accidentally committing files that should stay outside the repository.

## 4. Chapter 3: Working with Branches

For the next part, I created a branch called `eid-special`.

```bash
git branch eid-special
git switch eid-special
```

On that branch, I created two recipe files: `biryani.md` and `shemai.md`. I committed them separately so that each recipe had its own commit.

After finishing the recipes, I switched back to `main` and merged the branch.

```bash
git switch main
git merge eid-special
```

This helped me understand how branches allow us to work on separate tasks without making every change directly on the main branch.

### Resolving a Merge Conflict

I also practiced a merge conflict using `conflict-recipe.md`, which contained a Payesh recipe.

Two branches changed the sugar quantity differently. One used 2 tablespoons, while the other used 6 tablespoons. When I merged the branches, Git could not automatically decide which change to keep.

I opened the file, checked the conflicting lines, and resolved the conflict by keeping 4 tablespoons of sugar. Then I staged and committed the corrected file.

This was useful because it showed me that Git cannot resolve every conflict automatically. Sometimes we need to review the changes and decide what the final version should contain.

## 5. Chapter 4: Using GitHub

After learning the basics of local Git, I connected my repository to GitHub.

```bash
git remote add origin https://github.com/arifuzzaman-hredoy/DevOps-Module-2-Assignment.git
git push -u origin main
```

I then cloned the repository into another folder called `mitu-recipe-book`. I used this folder to simulate another person working on the same project.

In the cloned repository, Mitu added `chittagong-mezban.md` and pushed the change to GitHub. Later, another recipe, `sylheti-shakora.md`, was also added and pushed.

In my original repository, I used:

```bash
git fetch origin
git merge origin/main
```

I also practiced:

```bash
git pull origin main
```

### What Is the Difference Between Fetch and Pull?

I learned that `git fetch` downloads updates from the remote repository without automatically integrating them into my current branch.

`git merge` integrates changes from another branch into the current branch.

`git pull` fetches remote changes and then integrates them into the current branch.

This part helped me understand how changes can move between a local repository, GitHub, and another contributor's clone.

## 6. Chapter 5: Stash, File Organization, and Git History

### Saving Unfinished Work

While working on the Halua recipe, I had some unfinished changes. Instead of committing the incomplete recipe, I saved the work temporarily using:

```bash
git stash push -m "Save unfinished halua recipe"
```

I then updated the Biryani recipe by adding a resting time and a garnish instruction. I committed those changes before returning to the unfinished Halua work.

To restore the stashed changes, I used:

```bash
git stash pop
```

After that, I completed the Halua recipe and committed it.

This helped me understand how stash can be useful when I need to switch tasks without making an unfinished commit.

### Organizing the Recipe Files

As the project grew, I organized the recipes into separate folders based on their categories.

The final structure included:

```text
recipes/
├── rice-dishes/
│   └── biryani.md
├── sweets/
│   ├── halua.md
│   └── shemai.md
└── traditional/
    ├── bhapa-pitha.md
    ├── chittagong-mezban.md
    └── sylheti-shakora.md
```

I used `git mv` to move the recipe files into the correct directories. After organizing them, I committed the changes.

I also ran:

```bash
git log --stat -M
```

This allowed me to review file changes and see Git's rename detection in action.

### Removing an Old Recipe

I created a file called `old-recipe.md`, committed it, and then removed it using:

```bash
git rm old-recipe.md
git commit -m "Remove outdated pitha recipe draft"
```

I learned that `git rm` removes a tracked file and stages that removal for the next commit. Keeping the creation and deletion in separate commits also made the history easier to follow.

### Checking a Commit

I used the following command to inspect a particular commit:

```bash
git show 5c9f5ad
```

It displayed the Biryani improvement commit and the changes made in that commit.

### Practicing Reset on a Separate Branch

Finally, I created a branch called `reset-test` to practice `git reset --hard`.

```bash
git switch -c reset-test
git reset --hard 136cb87
```

The test branch moved back to the recipe organization commit. The later commits were no longer part of that branch's current history, but they remained in `main`.

I switched back to `main` afterward and checked the repository history.

I learned that `git reset --hard` can discard uncommitted tracked-file changes and move a branch to an earlier commit. It should be used carefully.

I also learned that rebasing a shared branch can cause problems because it rewrites commit history. Other contributors may still depend on the original commits.

Practicing reset on a separate branch helped me explore the command without intentionally moving the main branch backward.

## 7. Git Commands I Practiced

During this assignment, I practiced the following commands:

```bash
git init
git status
git add
git diff
git diff --staged
git commit
git reset
git branch
git switch
git merge
git remote -v
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

Each command helped me understand a different part of Git, from tracking everyday changes to managing branches and inspecting project history.

## 8. Final Checks

Before finishing the assignment, I checked the repository status, remote configuration, branches, and commit history.

Commands used:

```bash
git status
git remote -v
git branch
git log --oneline --graph --all
git status -sb
```

The final checks showed that:

* The local `main` branch was synchronized with `origin/main`.
* The working tree was clean.
* The required local branches were present.
* The commit history contained the work completed during the assignment.
* The `.gitignore` rules had been tested.
* The report had been committed and pushed to GitHub.
* The final Git history screenshot had been committed and pushed.

## 9. Screenshots

I captured and committed the following screenshot:

**1. Final Git History**

File: `screenshots/final-git-history.png`

This screenshot is intended to show the commit history and branch information.

I still need to add the following screenshots if separate evidence is required for each part of the assignment:

2. Git configuration and repository initialization.
3. `.gitignore` rules and verification.
4. Branch creation and merging.
5. Merge conflict and its resolution.
6. Remote repository operations.
7. Stash, recipe organization, and file deletion.
8. The `reset-test` experiment.

## 10. What I Learned

This assignment gave me practical experience with Git instead of only learning the commands theoretically.

I learned how to track changes, create commits, work with branches, resolve conflicts, and collaborate through GitHub. I also became more familiar with stash, file organization, and the risks of changing commit history.

One important thing I learned is that Git is not just about saving files. It also helps us understand what changed, when it changed, and how different versions of a project are connected.

Overall, this assignment helped me build a better foundation in Git and gave me more confidence in using version control for future DevOps projects.

**GitHub Repository:**
https://github.com/arifuzzaman-hredoy/DevOps-Module-2-Assignment
