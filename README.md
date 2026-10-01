# Git, GitHub & .NET CLI Cheat Sheet

A practical command reference for **Git**, **GitHub CLI**, and **.NET CLI**.

> Keep this README bookmarked whenever you forget a command.
> Copy, paste, and adapt as needed.

---

## 📚 Table of Contents

* [Git](#git)

  * [Configuration](#configuration)
  * [Repository](#repository)
  * [Status & History](#status--history)
  * [Add & Commit](#add--commit)
  * [Branch](#branch)
  * [Switch Branch](#switch-branch)
  * [Merge](#merge)
  * [Rebase](#rebase)
  * [Remote](#remote)
  * [Push & Pull](#push--pull)
  * [Fetch](#fetch)
  * [Stash](#stash)
  * [Undo Changes](#undo-changes)
  * [Reset & Revert](#reset--revert)
  * [Cherry Pick](#cherry-pick)
  * [Tag](#tag)
  * [Conflict](#conflict)
  * [Useful Commands](#useful-commands)
* [GitHub CLI](#github-cli)

  * [Authentication](#authentication)
  * [Repository](#repository-1)
  * [Pull Request](#pull-request)
  * [Issue](#issue)
  * [GitHub Actions](#github-actions)
* [.NET CLI](#net-cli)

  * [Information](#information)
  * [Create Project](#create-project)
  * [Solution](#solution)
  * [Build](#build)
  * [Run](#run)
  * [Watch](#watch)
  * [Restore](#restore)
  * [Clean](#clean)
  * [Test](#test)
  * [Publish](#publish)
  * [NuGet](#nuget)
  * [Project Reference](#project-reference)
  * [EF Core](#ef-core)
  * [Global Tools](#global-tools)
* [Common Workflows](#common-workflows)
* [Quick Reference](#quick-reference)
* [Important Notes](#important-notes)

---

# Git

## Configuration

Check Git version:

```bash
git --version
```

Check configuration:

```bash
git config --list
```

Set username:

```bash
git config --global user.name "Your Name"
```

Set email:

```bash
git config --global user.email "your@email.com"
```

Set default branch:

```bash
git config --global init.defaultBranch main
```

Check username:

```bash
git config user.name
```

Check email:

```bash
git config user.email
```

---

## Repository

Initialize repository:

```bash
git init
```

Clone repository:

```bash
git clone <repository-url>
```

Clone specific branch:

```bash
git clone -b <branch-name> <repository-url>
```

Clone into a specific directory:

```bash
git clone <repository-url> <folder-name>
```

---

## Status & History

Check status:

```bash
git status
```

Short status:

```bash
git status --short
```

View commit history:

```bash
git log
```

Compact history:

```bash
git log --oneline
```

Graph:

```bash
git log --oneline --graph --decorate --all
```

Show last 10 commits:

```bash
git log -10
```

Show commit:

```bash
git show <commit-hash>
```

Search commit messages:

```bash
git log --grep="keyword"
```

Search commits by author:

```bash
git log --author="name"
```

---

## Add & Commit

Add a file:

```bash
git add <file>
```

Add multiple files:

```bash
git add file1.cs file2.cs
```

Add all changes:

```bash
git add .
```

Add all tracked changes:

```bash
git add -u
```

Commit:

```bash
git commit -m "your commit message"
```

Add and commit tracked files:

```bash
git commit -am "your commit message"
```

Amend the last commit:

```bash
git commit --amend
```

Amend commit message:

```bash
git commit --amend -m "new message"
```

---

## Branch

List local branches:

```bash
git branch
```

List all branches:

```bash
git branch -a
```

List remote branches:

```bash
git branch -r
```

Create branch:

```bash
git branch <branch-name>
```

Delete local branch:

```bash
git branch -d <branch-name>
```

Force delete local branch:

```bash
git branch -D <branch-name>
```

Rename current branch:

```bash
git branch -m <new-name>
```

---

## Switch Branch

Switch branch:

```bash
git switch <branch-name>
```

Create and switch:

```bash
git switch -c <branch-name>
```

Legacy syntax:

```bash
git checkout <branch-name>
```

Create and checkout:

```bash
git checkout -b <branch-name>
```

---

## Merge

Merge branch:

```bash
git merge <branch-name>
```

No fast-forward merge:

```bash
git merge --no-ff <branch-name>
```

Abort merge:

```bash
git merge --abort
```

Example:

```bash
git switch dev
git merge feature/login
```

---

## Rebase

Rebase current branch:

```bash
git rebase <branch-name>
```

Example:

```bash
git switch feature/login
git rebase dev
```

Interactive rebase:

```bash
git rebase -i HEAD~3
```

Continue:

```bash
git add .
git rebase --continue
```

Abort:

```bash
git rebase --abort
```

Skip:

```bash
git rebase --skip
```

---

## Remote

Show remotes:

```bash
git remote -v
```

Add remote:

```bash
git remote add origin <repository-url>
```

Change remote URL:

```bash
git remote set-url origin <repository-url>
```

Remove remote:

```bash
git remote remove origin
```

Show remote information:

```bash
git remote show origin
```

---

## Push & Pull

Push:

```bash
git push
```

Push specific branch:

```bash
git push origin <branch-name>
```

Push and set upstream:

```bash
git push -u origin <branch-name>
```

Force push:

```bash
git push --force
```

Safer force push:

```bash
git push --force-with-lease
```

Delete remote branch:

```bash
git push origin --delete <branch-name>
```

Pull:

```bash
git pull
```

Pull specific branch:

```bash
git pull origin <branch-name>
```

Pull with rebase:

```bash
git pull --rebase
```

---

## Fetch

Fetch changes:

```bash
git fetch
```

Fetch all remotes:

```bash
git fetch --all
```

Fetch and remove deleted remote branches:

```bash
git fetch --all --prune
```

Fetch specific branch:

```bash
git fetch origin <branch-name>
```

---

## Stash

Save changes:

```bash
git stash
```

Save with message:

```bash
git stash push -m "message"
```

Include untracked files:

```bash
git stash -u
```

List stashes:

```bash
git stash list
```

Apply latest stash:

```bash
git stash apply
```

Apply specific stash:

```bash
git stash apply stash@{0}
```

Apply and remove stash:

```bash
git stash pop
```

Delete stash:

```bash
git stash drop stash@{0}
```

Delete all stashes:

```bash
git stash clear
```

---

## Undo Changes

Discard changes in a file:

```bash
git restore <file>
```

Discard all unstaged changes:

```bash
git restore .
```

Unstage a file:

```bash
git restore --staged <file>
```

Unstage everything:

```bash
git restore --staged .
```

---

## Reset & Revert

Soft reset:

```bash
git reset --soft HEAD~1
```

Mixed reset:

```bash
git reset HEAD~1
```

Hard reset:

```bash
git reset --hard HEAD~1
```

Reset to a specific commit:

```bash
git reset --hard <commit-hash>
```

Create a new commit that reverses another commit:

```bash
git revert <commit-hash>
```

> Use `git revert` when the commit has already been pushed/shared.
>
> Use `git reset` when you need to rewrite your local history.

---

## Cherry Pick

Apply a specific commit:

```bash
git cherry-pick <commit-hash>
```

Apply multiple commits:

```bash
git cherry-pick <hash1> <hash2>
```

Apply a range:

```bash
git cherry-pick <oldest-hash>^..<newest-hash>
```

Continue:

```bash
git add .
git cherry-pick --continue
```

Abort:

```bash
git cherry-pick --abort
```

---

## Tag

Create tag:

```bash
git tag v1.0.0
```

Create annotated tag:

```bash
git tag -a v1.0.0 -m "Version 1.0.0"
```

List tags:

```bash
git tag
```

Push tag:

```bash
git push origin v1.0.0
```

Push all tags:

```bash
git push origin --tags
```

Delete local tag:

```bash
git tag -d v1.0.0
```

Delete remote tag:

```bash
git push origin --delete v1.0.0
```

---

## Conflict

Check conflicted files:

```bash
git status
```

After resolving conflicts:

```bash
git add .
```

For merge:

```bash
git commit
```

For rebase:

```bash
git rebase --continue
```

For cherry-pick:

```bash
git cherry-pick --continue
```

Abort merge:

```bash
git merge --abort
```

Abort rebase:

```bash
git rebase --abort
```

Abort cherry-pick:

```bash
git cherry-pick --abort
```

---

## Useful Commands

Show unstaged changes:

```bash
git diff
```

Show staged changes:

```bash
git diff --staged
```

Compare branches:

```bash
git diff main..dev
```

Find who changed a line:

```bash
git blame <file>
```

Find lost commits:

```bash
git reflog
```

Preview untracked files that can be removed:

```bash
git clean -n
```

Remove untracked files:

```bash
git clean -f
```

Remove untracked files and directories:

```bash
git clean -fd
```

---

# GitHub CLI

> Requires [GitHub CLI](https://cli.github.com/) (`gh`).

Check version:

```bash
gh --version
```

---

## Authentication

Login:

```bash
gh auth login
```

Check authentication:

```bash
gh auth status
```

Logout:

```bash
gh auth logout
```

---

## Repository

View repository:

```bash
gh repo view
```

Open repository in browser:

```bash
gh repo view --web
```

Clone repository:

```bash
gh repo clone <owner>/<repo>
```

Create repository:

```bash
gh repo create
```

Create public repository:

```bash
gh repo create <repo-name> --public
```

Create private repository:

```bash
gh repo create <repo-name> --private
```

Fork repository:

```bash
gh repo fork <owner>/<repo>
```

---

## Pull Request

List pull requests:

```bash
gh pr list
```

View pull request:

```bash
gh pr view <number>
```

Open PR in browser:

```bash
gh pr view <number> --web
```

Create pull request:

```bash
gh pr create
```

Create PR with title and body:

```bash
gh pr create \
  --title "Add feature" \
  --body "Description"
```

Checkout PR:

```bash
gh pr checkout <number>
```

Review PR:

```bash
gh pr review <number>
```

Approve PR:

```bash
gh pr review <number> --approve
```

Request changes:

```bash
gh pr review <number> \
  --request-changes \
  --body "Please fix..."
```

Merge PR:

```bash
gh pr merge <number>
```

Squash merge:

```bash
gh pr merge <number> --squash
```

---

## Issue

List issues:

```bash
gh issue list
```

View issue:

```bash
gh issue view <number>
```

Create issue:

```bash
gh issue create
```

Close issue:

```bash
gh issue close <number>
```

Reopen issue:

```bash
gh issue reopen <number>
```

---

## GitHub Actions

List workflow runs:

```bash
gh run list
```

View workflow run:

```bash
gh run view <run-id>
```

Watch workflow:

```bash
gh run watch
```

Run workflow manually:

```bash
gh workflow run <workflow-name>
```

Cancel workflow:

```bash
gh run cancel <run-id>
```

---

# .NET CLI

## Information

Check .NET version:

```bash
dotnet --version
```

List installed SDKs:

```bash
dotnet --list-sdks
```

List installed runtimes:

```bash
dotnet --list-runtimes
```

Show environment information:

```bash
dotnet --info
```

Show help:

```bash
dotnet --help
```

---

## Create Project

Create console application:

```bash
dotnet new console -n MyApp
```

Create ASP.NET Core Web API:

```bash
dotnet new webapi -n MyApi
```

Create ASP.NET Core Web App:

```bash
dotnet new webapp -n MyWebApp
```

Create Blazor application:

```bash
dotnet new blazor -n MyBlazorApp
```

Create class library:

```bash
dotnet new classlib -n MyLibrary
```

List templates:

```bash
dotnet new list
```

Search templates:

```bash
dotnet new search <keyword>
```

---

## Solution

Create solution:

```bash
dotnet new sln -n MySolution
```

Add project:

```bash
dotnet sln add MyProject/MyProject.csproj
```

Add multiple projects:

```bash
dotnet sln add MyProject/*.csproj
```

List projects:

```bash
dotnet sln list
```

Remove project:

```bash
dotnet sln remove MyProject/MyProject.csproj
```

---

## Build

Build project:

```bash
dotnet build
```

Build specific project:

```bash
dotnet build MyProject.csproj
```

Release build:

```bash
dotnet build -c Release
```

Build without restore:

```bash
dotnet build --no-restore
```

---

## Run

Run project:

```bash
dotnet run
```

Run specific project:

```bash
dotnet run --project MyProject
```

Run without restore:

```bash
dotnet run --no-restore
```

Run Release:

```bash
dotnet run -c Release
```

Pass arguments:

```bash
dotnet run -- arg1 arg2
```

---

## Watch

Run with Hot Reload:

```bash
dotnet watch
```

Watch a specific project:

```bash
dotnet watch --project MyProject
```

Watch without restore:

```bash
dotnet watch --no-restore
```

---

## Restore

Restore dependencies:

```bash
dotnet restore
```

Restore specific project:

```bash
dotnet restore MyProject.csproj
```

Ignore failed package sources:

```bash
dotnet restore --ignore-failed-sources
```

---

## Clean

Clean project:

```bash
dotnet clean
```

Clean Release:

```bash
dotnet clean -c Release
```

---

## Test

Run tests:

```bash
dotnet test
```

Run specific test project:

```bash
dotnet test MyTests.csproj
```

Run without build:

```bash
dotnet test --no-build
```

Run Release tests:

```bash
dotnet test -c Release
```

Detailed output:

```bash
dotnet test --verbosity detailed
```

---

## Publish

Publish application:

```bash
dotnet publish
```

Publish Release:

```bash
dotnet publish -c Release
```

Publish to specific directory:

```bash
dotnet publish -c Release -o ./publish
```

Self-contained:

```bash
dotnet publish \
  -c Release \
  --self-contained true
```

Framework-dependent:

```bash
dotnet publish \
  -c Release \
  --self-contained false
```

Specify runtime:

```bash
dotnet publish \
  -c Release \
  -r win-x64
```

Single-file application:

```bash
dotnet publish \
  -c Release \
  -r win-x64 \
  --self-contained true \
  /p:PublishSingleFile=true
```

---

## NuGet

List packages:

```bash
dotnet list package
```

Add package:

```bash
dotnet add package Newtonsoft.Json
```

Add specific version:

```bash
dotnet add package Newtonsoft.Json --version 13.0.3
```

Remove package:

```bash
dotnet remove package Newtonsoft.Json
```

List outdated packages:

```bash
dotnet list package --outdated
```

List vulnerable packages:

```bash
dotnet list package --vulnerable
```

---

## Project Reference

Add project reference:

```bash
dotnet add MyApi reference MyLibrary
```

Remove project reference:

```bash
dotnet remove MyApi reference MyLibrary
```

List project references:

```bash
dotnet list MyApi reference
```

---

# EF Core

Install EF Core CLI:

```bash
dotnet tool install --global dotnet-ef
```

Update EF Core CLI:

```bash
dotnet tool update --global dotnet-ef
```

Check EF version:

```bash
dotnet ef --version
```

Create migration:

```bash
dotnet ef migrations add InitialCreate
```

Update database:

```bash
dotnet ef database update
```

Remove last migration:

```bash
dotnet ef migrations remove
```

List migrations:

```bash
dotnet ef migrations list
```

Generate SQL:

```bash
dotnet ef migrations script
```

Drop database:

```bash
dotnet ef database drop
```

Specify DbContext:

```bash
dotnet ef migrations add InitialCreate \
  --context AppDbContext
```

---

## EF Core: Separate Projects

When the `DbContext` project and startup project are different:

```bash
dotnet ef migrations add InitialCreate \
  --project Data \
  --startup-project API
```

Update database:

```bash
dotnet ef database update \
  --project Data \
  --startup-project API
```

---

# Global Tools

List global tools:

```bash
dotnet tool list --global
```

Install global tool:

```bash
dotnet tool install --global <tool-name>
```

Update global tool:

```bash
dotnet tool update --global <tool-name>
```

Uninstall global tool:

```bash
dotnet tool uninstall --global <tool-name>
```

Restore local tools:

```bash
dotnet tool restore
```

---

# Common Workflows

## Clone & Run .NET Project

```bash
git clone <repository-url>

cd <project-folder>

dotnet restore

dotnet build

dotnet run
```

---

## Start a Feature

```bash
git switch dev

git pull

git switch -c feature/my-feature
```

Work on the code, then:

```bash
git status

git add .

git commit -m "Add my feature"

git push -u origin feature/my-feature
```

---

## Update Feature Branch

```bash
git switch dev

git pull

git switch feature/my-feature

git rebase dev
```

After resolving conflicts:

```bash
git add .

git rebase --continue
```

Then:

```bash
git push --force-with-lease
```

---

## Typical .NET Development Loop

```bash
dotnet restore

dotnet build

dotnet watch
```

Run tests separately:

```bash
dotnet test
```

Build for production:

```bash
dotnet publish -c Release
```

---

# Quick Reference

| Task               | Command                           |
| ------------------ | --------------------------------- |
| Git status         | `git status`                      |
| Add all            | `git add .`                       |
| Commit             | `git commit -m "message"`         |
| Push               | `git push`                        |
| Pull               | `git pull`                        |
| Fetch              | `git fetch --all --prune`         |
| List branches      | `git branch -a`                   |
| Create branch      | `git switch -c <branch>`          |
| Switch branch      | `git switch <branch>`             |
| Merge              | `git merge <branch>`              |
| Rebase             | `git rebase <branch>`             |
| Stash              | `git stash`                       |
| Apply stash        | `git stash pop`                   |
| Undo local commit  | `git reset --soft HEAD~1`         |
| Undo pushed commit | `git revert <hash>`               |
| Find lost commits  | `git reflog`                      |
| GitHub PR list     | `gh pr list`                      |
| GitHub PR create   | `gh pr create`                    |
| GitHub Actions     | `gh run list`                     |
| .NET build         | `dotnet build`                    |
| .NET run           | `dotnet run`                      |
| .NET watch         | `dotnet watch`                    |
| .NET restore       | `dotnet restore`                  |
| .NET test          | `dotnet test`                     |
| .NET publish       | `dotnet publish -c Release`       |
| Add NuGet          | `dotnet add package <name>`       |
| EF migration       | `dotnet ef migrations add <name>` |
| EF database update | `dotnet ef database update`       |

---

# Important Notes

## `reset` vs `revert`

Use:

```bash
git revert <commit>
```

when the commit has already been pushed or shared with other developers.

Use:

```bash
git reset
```

when you need to move your local branch backward.

---

## `--force` vs `--force-with-lease`

Avoid using:

```bash
git push --force
```

when possible.

Prefer:

```bash
git push --force-with-lease
```

`--force-with-lease` helps prevent accidentally overwriting remote changes you haven't seen.

---

## `merge` vs `rebase`

Merge:

```bash
git merge dev
```

Rebase:

```bash
git rebase dev
```

Both integrate changes, but they produce different commit histories.

---

# 🧯 Emergency Commands

## Accidentally committed

Keep changes but undo the commit:

```bash
git reset --soft HEAD~1
```

Undo commit and unstage changes:

```bash
git reset HEAD~1
```

Completely remove the commit and local changes:

```bash
git reset --hard HEAD~1
```

> ⚠️ Be careful with `--hard`.

---

## Accidentally deleted something

Check the reflog:

```bash
git reflog
```

Then restore the desired state:

```bash
git reset --hard <commit-hash>
```

---

## Accidentally pushed a bad commit

Create a new reverse commit:

```bash
git revert <commit-hash>

git push
```

---

# 📌 Daily Cheat Sheet

Most development sessions only need a handful of commands.

### Git

```bash
git status

git pull

git switch <branch>

git add .

git commit -m "message"

git push
```

### .NET

```bash
dotnet restore

dotnet build

dotnet watch

dotnet test

dotnet publish -c Release
```

### GitHub

```bash
gh pr list

gh pr create

gh pr checkout <number>

gh pr merge <number>

gh run list
```

---

# 📖 Resources

* [Git Documentation](https://git-scm.com/docs)
* [GitHub CLI Documentation](https://cli.github.com/manual/)
* [.NET CLI Documentation](https://learn.microsoft.com/dotnet/core/tools/)
* [ASP.NET Core Documentation](https://learn.microsoft.com/aspnet/core/)
* [Entity Framework Core Documentation](https://learn.microsoft.com/ef/core/)
* [NuGet Documentation](https://learn.microsoft.com/nuget/)

---

## License

This cheat sheet is provided for personal and educational use.
