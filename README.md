# Git It!
Chilling out, maxin' and relaxing all cool with Git.

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

### Revert
If commits have been pushed and need to be reverted.
```
git reset --hard fa74044346b1248d9f176c87dc457ceceea9024a
```

### Caching
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
