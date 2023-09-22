
# Hooks

This repository contains git commit hooks utilized for local developement and / or CI workflows.

In some cases, the commit hooks here can be used independently as stand-alone scripts by copying them into the proper subdirectory under the `.git` directory in your project's repository.

A better, and suggested approach, is to leverage the [pre-commit.com](https://pre-commit.com) tooling as shown in the [Getting Started](#getting-started) section.

## Getting Started

### Prerequisites

* pre-commit: Check out the installation documentation [here](https://pre-commit.com/#install)

### Using hooks

To start, in the repository in which you wish to utilize these commit hook scripts, create a `.pre-commit-config.yaml` containing the following:

```
repos:
  - repo: https://github.com/enterprise-contract/hooks
    rev: v0.0.1
    hooks:
      - id: check-commit-message
```
Execute the following at the root of your project:
```
$ pre-commit install -t commit-msg
``` 

At this point, executing `git commit` will trigger the `check-commit-msg` hook, which validates that the commit message contains reference to a ticket or issue in one of the following formats:

|if your commit|use this keyword|value|
|-|-------|-----|
|resolves an issue/ticket|resolves, res, resolved| !123(only for GitHub Issues), PROJ-1234|
|only references an issue/ticket|ref, refs, references, refers to| !123(only for GitHub Issues), PROJ-1234|

*Example git commit message*:
```
Fixed the pesky bug.

This commit fixed that pesky bug that we all hated.

resolves: PROJ-1234
Signed-off-by: John Doe <jdoe@example.com>

# Please enter the commit message for your changes. Lines starting 
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date: Fri Jan 10 00:00:00 2025 -0400
#
# On branch PROJ-1234
```

### Creating new hooks

We recommend reviewing the precommit.com documentation on [creating new hooks](https://pre-commit.com/#new-hooks)

For organizational purposes, if your hook is file based (script, python, golang, etc)create a directory corresponding the to the hook type or add your hook to an existing directory.

See [this link](https://git-scm.com/docs/githooks#_hooks) for hook types.

## Questions or Issues?
Feel free to post a [question](https://github.com/enterprise-contract/hooks/discussions) or open an [issue](https://github.com/enterprise-contract/hooks/issues) if you have questions any issues.