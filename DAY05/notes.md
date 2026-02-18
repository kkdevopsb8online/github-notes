# Difference Between Branch and Tag in Git

## Branch

* Mutable (can change over time)
* Created during development
* Can be created from another branch
* Mainly used for feature development, bug fixes, and enhancements

### Common Branch Commands

```bash
git branch                  # List branches
git branch <branch-name>    # Create a branch
git push <alias> <branch>   # Push branch to remote
git push <alias> --all      # Push all branches
git branch -d <branch>      # Delete branch
```

---

## Tag

* Immutable (cannot be changed once created)
* Usually created after production deployment
* Mostly created from master/main branch
* Used to mark version releases (major.minor.patch)

### Common Tag Commands

```bash
git tag                     # List tags
git tag <tag-name>          # Create tag
git push <alias> <tag>      # Push specific tag
git push <alias> --tags     # Push all tags
git tag -d <tag-name>       # Delete local tag
```

---

## Example: Creating a Version Tag

```bash
Step 1: git tag                     # Check existing tags
Step 2: git checkout master
Step 3: git tag Airtel_V1.0.0       # Major.Minor.Patch format
Step 4: git tag                     # Verify tag
Step 5: git push airtel Airtel_V1.0.0
```

Note: In repository hosting platforms, tag versions are usually available for download as zip or tar files.

---

## Interview Question

How to create a tag in a remote repository?

Tags are created locally first and then pushed to remote.

In GitHub:
Go to Releases → Create Release → Create Tag → Publish Release.

---

# Git Stash

Scenario:
You are working on the dev branch. Suddenly you get an issue in production (master branch). You need to switch branches but your current work is incomplete.

## Save Current Work

```bash
git stash save "login feature"
```

## View Stash List

```bash
git stash list
```

Example output:
stash@{0}
stash@{1}

## Switch to Master and Fix Issue

```bash
git checkout master
```

After completing the fix, switch back to dev.

## Apply Stashed Changes

```bash
git stash apply stash@{1}
```

---

## Reducing Local Repository Size

If your local repository size increases due to unused stashes:

Delete latest stash:

```bash
git stash drop
```

Delete specific stash:

```bash
git stash drop stash@{5}
```

Apply and delete at same time:

```bash
git stash pop
```

Delete all stashes:

```bash
git stash clear
```

---

# Restore Working Area Changes

If you mistakenly modified a file and want to restore it:

```bash
git restore <file-name>
```

This restores the file to the last committed state.

