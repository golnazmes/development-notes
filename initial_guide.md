
# Development Guide

## How to Edit Your Commits Interactively in VSCode

You can use the following command to start an interactive rebase:

```bash
gitv rebase -i HEAD~8
```
`gitv` is an alias for "GIT_EDITOR=\"code --wait\" git" 
The environment variable GIT_EDITOR needs to be an executable of some text editor (default is nano for most systems, vi for some others). And vscode needs a commandline flag --wait to tell it to freeze the parent process until the file has been closed. Then otherwise, it just calls the git executable.
With bash, you can modify environment variables on a per-command basis by prefacing the command with the env variable:
ENV_VAR=value git commit -m "..."
or you could set the environment variable for the lifespan of the bash session using
export ENV_VAR=value
I don't prefer this approach since 95% of the time, I want git to just use nano 
These commands mean:
- **e (edit)**: Edit the commit message or the content.
- **fixup**: Combine the commit with the previous one and discard the commit message.
- **s (squash)**: Combine the commit with the previous one, but keep both commit messages.
- **r (reword)**: Change the commit message of the commit.

## What Does Git Pull Actually Do?

`git pull` consists of two commands:
1. `git fetch origin main`: Updates your local repository with changes from the remote repository.
2. Based on your configuration, it follows with either:
   - `git merge origin/main`: Merges the fetched changes into your local branch.
   - `git rebase origin/main`: Reapplies your local commits on top of the fetched changes.
You can change the configuration using `git config`

## How to Sync a Fork with Command Line Without GitHub User Interface

To sync your fork with the upstream repository, use:

```bash
git pull upstream main
```

## What is a Pre-commit Hook?

A pre-commit hook is a script located in `.git/hooks` that runs automatically before a commit is made. It is typically used to enforce certain rules, run tests, or lint the code.

## What Does `git commit --no-verify` Do?

The `git commit --no-verify` command bypasses the pre-commit and commit-msg hooks. These hooks, which run automatically before a commit, are used to enforce rules, run tests, or lint code. Using `--no-verify` allows you to commit changes without running these hooks, which can be useful when you need to make a quick commit and plan to address the issues flagged by the hooks later, or the hooks are malfunctioning or not relevant to the changes you are making.

## How to Check Your Code's Style

To check your code's style, you can use `ruff`, a tool for linting:

```bash
pip install ruff
ruff check directory
```


## Different Types of Tests

**Performance Test**  
Assesses system speed, responsiveness, and stability under load. Ensures the system meets performance benchmarks.

**Unit Test**  
Tests individual components or functions in isolation. Ensures each part works correctly on its own.

**Integration Test**  
Checks that combined components work together as expected. Ensures proper interaction between different system parts.

**Regression Test**  
Verifies recent changes haven’t broken existing functionality. Ensures software remains stable after updates. (#TODO:am i right?)

**Acceptance Test**  
Validates the system against basic requirements and user needs. Ensures the software meets the criteria for delivery and fulfills its intended purpose for end-users.

**End-to-End Test**  
Tests the entire application flow from start to finish. Simulates real user scenarios to ensure all integrated components work together seamlessly in a production-like environment.

## How to Deal with Sharding in JAX for Checkpointing Systems
#TODO
