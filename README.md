# Git It! <!-- omit in toc -->
Chilling out, maxin' and relaxing all cool with Git.

## Contents <!-- omit in toc -->
- [Staging](#staging)
- [Rebasing](#rebasing)
  - [Interactive Rebasing](#interactive-rebasing)
- [Reset](#reset)
- [Revert](#revert)
- [Commit Messages](#commit-messages)
- [Caching](#caching)
- [Graph](#graph)

### Staging
To add code to staging in partials rather than the entire file.

* `y` - stage this hunk
* `n` - do not stage this hunk
* `a` - stage this and all the remaining hunks in the file
* `d` - do not stage this hunk nor any of the remaining hunks in the file

```
git add -p
```
### Rebasing
To cancel a rebase: `git rebase --abort`.

```
git rebase master
git add [FILENAME.ext]
git rebase --continue
```

#### Interactive Rebasing
Pull the latest changes to master.

```
git rebase -i master
```

You must rebase onto a particular commit.

With a non-interactive rebase, if you supply a direct ancestor of the current commit then you aren't changing anything; with an interactive rebase you can edit commits after the commit that you are rebasing onto, even if the commit is a direct ancestor of your current commit but you do have to specify this commit that you want to edit onwards from.

Without a commit range, `rebase -i` will show `noop` as the message and won't display any commits.
To edit the last, say, 10 commits, use the following:

```
git rebase -i HEAD~10
```

This will show a list of commits, each commit starting with the word pick.

```
pick e5266359e Add check for Support plan type to hide Salesforce integration on Essential plans
pick 892b8cfad Initial logic to identity Essentials plan in Support
pick b75eaef89 Testing routes and enabledChecks
pick a179b26b9 pass accountProducts down to enable-check.ts
pick 7251e57a5 Conditional rendering based on enabled check for isNotEssentialPlan
```

In Vim:
* Type `cw` and then a new word (such as `s` to squash) then press `Esc` to change word at the start of the commit.
* After all commits have been updated, type `wq` to write/save the changes and quit.
* In each commit message, press `i` to edit the commit message, then `Esc` to exit.
* After all commits have been updated, type `wq` to write/save the changes and quit.
* Use `git log` and `git status` to confirm current history.

### Reset
If local branch and remote origin/branch-name have diverged so much, with different commits respectively, that it doesn't make sense to try and resolve all the conflicts, we can reset the local branch to whatever is on origin.

To do this, we'll need to fetch from the master, then checkout to the branch and run:
```
git reset --hard origin/branch-name
```

Further explanation is available [here](https://stackoverflow.com/questions/43037293/what-is-the-difference-between-git-pull-and-git-reset-hard-origin-branch/43037318#43037318) on Stack Overflow.

### Revert
If commits have been pushed and need to be reverted.
```
git reset --hard fa74044346b1248d9f176c87dc457ceceea9024a
```

### Commit Messages
* `FIRST`: Initial commit
* `DOC`: Add link to deployment video
* `FIX`: Add condition before triggering last signin request
* `CONFIG`: Add npm script fo configuring environment variables from .env
* `NEW`: Add attendance feature to frontend and backend
* `QUALITY`: Move passport logic to config file
* `LOOKS`: Add styling for code snippets in .md files
* `ENHANCE`: Add dynamic title for all pages

Amend last commit message after pushing:
```
git commit --amend -m "fix: Make test command visible in ZOAAS"
```

### Caching
Remove a specific file from Git cache:
```
git rm [FILENAME] --cached
```

Remove all files from Git cache:
```
git rm -r --cached .
```

* Update `.gitignore`
* `git add` files to be staged

### Graph
```
git log --graph
```
