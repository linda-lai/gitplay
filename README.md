# Git <!-- omit in toc -->
Chilling out, maxin' and relaxing all cool with Git.

- [Conventional Commits](#conventional-commits)
- [Tutorials](#tutorials)
- [Helpful Commands](#helpful-commands)
  - [Caching](#caching)
  - [Commit Messages](#commit-messages)
  - [Fetch & Pull](#fetch--pull)
  - [Graph](#graph)
  - [Rebasing](#rebasing)
    - [Interactive Rebasing](#interactive-rebasing)
  - [Reset](#reset)
  - [Revert](#revert)
  - [Staging](#staging)
  - [Caching](#caching-1)
  - [Stashing](#stashing)

## Conventional Commits
* [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.2/): A specification for adding human and machine readable meaning to commit messages.
* [Patterns for writing better git commit messages](https://dev.to/helderburato/patterns-for-writing-better-git-commit-messages-4ba0): Suggested patterns and ways of writing Git commit messages.

To write a standardised commit message, it should be structured as follows:

```
<type>[optional scope]: <description>

[optional body]

[optional footer]
```

The commit contains the following structural elements, to communicate intent to the consumers of your library:

* `fix`: a commit of the type fix patches a bug in your codebase (this correlates with PATCH in semantic versioning).
* `feat`: a commit of the type feat introduces a new feature to the codebase (this correlates with MINOR in semantic versioning).
* `BREAKING CHANGE`: a commit that has the text BREAKING CHANGE: at the beginning of its optional body or footer section introduces a breaking API change (correlating with MAJOR in semantic versioning). A breaking change can be part of commits of any type. e.g., a fix:, feat: & chore: types would all be valid, in addition to any other type.
* Others: commit types other than `fix:` and `feat:` are recommend, for example `chore:`, `docs:`, `style:`, `refactor:`, `perf:`, `test:`, and others. We also recommend improvement for commits that improve a current implementation without adding a new feature or fixing a bug. Notice these types are not mandated by the conventional commits specification, and have no implicit effect in semantic versioning (unless they include a BREAKING CHANGE, which is NOT recommended).
* A scope may be provided to a commit’s type, to provide additional contextual information and is contained within parenthesis, e.g., `feat(parser): add ability to parse arrays`.

## Tutorials
* [Happy Git](https://happygitwithr.com/index.html): Using Git and GitHub with R, Rstudio, and R Markdown.


## Helpful Commands
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

### Fetch & Pull
Fetch your latest changes onto a branch without having to do a merge commit, and apply your commits to the top of the remote tree.

```
git pull --rebase
```

### Graph
```
git log --graph
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

### Staging
To add code to staging in partials rather than the entire file.

* `y` - stage this hunk
* `n` - do not stage this hunk
* `a` - stage this and all the remaining hunks in the file
* `d` - do not stage this hunk nor any of the remaining hunks in the file

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
git add -p
```

### Stashing
To apply multiple Git stashes at once (i.e. changes stashed using `git stash`), pop the first stash:

```
git stash pop
```

Temporarily commit the changes from the first stash:
```
git add . && git commit -m "WIP"
```

Pop the second stash:
```
git stash pop
```

Undo the temporary commit, but keeping the changes it introduced:
```
git reset --soft HEAD^
```
