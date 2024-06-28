
# Development Guide

## How to Edit Your Commits Interactively in VSCode

You can use the following command to start an interactive rebase:

```bash
git rebase -i HEAD~8
```

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

## How to Sync a Fork with Command Line Without GitHub User Interface

To sync your fork with the upstream repository, use:

```bash
git pull upstream main
```

## What is a Pre-commit Hook?

A pre-commit hook is a script located in `.git/hooks` that runs automatically before a commit is made. It is typically used to enforce certain rules, run tests, or lint the code.

## What Does `git commit --no-verify` Do?

The `git commit --no-verify` command bypasses the pre-commit and commit-msg hooks. These hooks, which run automatically before a commit, are used to enforce rules, run tests, or lint code. Using `--no-verify` allows you to commit changes without running these hooks, which can be useful when:
- You need to make a quick commit and plan to address the issues flagged by the hooks later.
- The hooks are malfunctioning or not relevant to the changes you are making.

## How to Check Your Code's Style

To check your code's style, you can use `ruff`, a tool for linting:

```bash
pip install ruff
ruff check recommence/ tests/
```

This command installs `ruff` and runs it to check the style of code located in the `recommence/` and `tests/` directories.

## Different Types of Tests

**Performance Test**  
Assesses system speed, responsiveness, and stability under load. Ensures the system meets performance benchmarks.

**Unit Test**  
Tests individual components or functions in isolation. Ensures each part works correctly on its own.

**Integration Test**  
Checks that combined components work together as expected. Ensures proper interaction between different system parts.

**Regression Test**  
Verifies recent changes haven’t broken existing functionality. Ensures software remains stable after updates.

**Acceptance Test**  
Validates the system against business requirements and user needs. Ensures the software meets the criteria for delivery and fulfills its intended purpose for end-users.

**End-to-End Test**  
Tests the entire application flow from start to finish. Simulates real user scenarios to ensure all integrated components work together seamlessly in a production-like environment.

## How to Deal with Sharding in JAX for Checkpointing Systems

When dealing with sharding in JAX for checkpointing systems, you need to ensure that the checkpointing process correctly handles distributed data across multiple devices. Strategies include:
- Aggregating data to a single device for checkpointing.
- Implementing a distributed checkpointing mechanism that writes and reads sharded data efficiently.
