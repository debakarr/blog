---
title: "Day 7: Basic Git commands (`git init`, `git add`, `git commit`, `git status`)"
date: 2023-04-22T17:43:13+05:30
draft: false
author: Debakar Roy
authorLink: https://github.com/debakarr
tags: ["DevOps", "Git", "GitHub", "Tutorial", "How-to"] 
categories: ["DevOps", "Software Development", "Automation", "Infrastructure", "Git"]
---

{{< admonition type=info title="Planned Content" open=false >}}

**Part 1: Introduction to DevOps**

*   Day 1: Understanding DevOps, its principles, and benefits
*   Day 2: Exploring the DevOps lifecycle and its stages
*   Day 3: Introduction to Continuous Integration (CI) and Continuous Deployment (CD)
*   Day 4: Familiarizing with common DevOps tools and technologies
*   Day 5: Studying DevOps culture and best practices

**Part 2: Version Control Systems**

*   Day 6: Introduction to Git
*   **Day 7: Basic Git commands (`git init`, `git add`, `git commit`, `git status`)**
*   Day 8: Branching and merging in Git
*   Day 9: Remote repositories and collaboration with Git
*   Day 10: Git workflows and best practices

**Part 3: Continuous Integration and Continuous Deployment (CI/CD)**

*   Day 11: Introduction to CI/CD
*   Day 12: Jenkins - Installation and configuration
*   Day 13: Jenkins - Creating and managing jobs
*   Day 14: Jenkins - Integrating with Git
*   Day 15: Jenkins - Pipelines and best practices

**Part 4: Configuration Management**

*   Day 16: Introduction to configuration management
*   Day 17: Ansible - Installation and configuration
*   Day 18: Ansible - Ad-hoc commands and playbooks
*   Day 19: Ansible - Roles and best practices
*   Day 20: Puppet and Chef - Overview and comparison

**Part 5: Infrastructure as Code**

*   Day 21: Introduction to Infrastructure as Code (IaC)
*   Day 22: Terraform - Installation and configuration
*   Day 23: Terraform - Writing and applying configuration files
*   Day 24: Terraform - Modules and best practices
*   Day 25: CloudFormation (AWS) - Overview and comparison

**Part 6: Containerization**

*   Day 26: Introduction to containerization
*   Day 27: Docker - Installation and configuration
*   Day 28: Docker - Building and managing images
*   Day 29: Docker - Running and managing containers
*   Day 30: Docker Compose and best practices

**Part 7: Container Orchestration**

*   Day 31: Introduction to container orchestration
*   Day 32: Kubernetes - Architecture and components
*   Day 33: Kubernetes - Deployments, services, and storage
*   Day 34: Kubernetes - ConfigMaps and secrets
*   Day 35: Kubernetes - Best practices and Helm

**Part 8: Monitoring and Logging**

*   Day 36: Introduction to monitoring and logging
*   Day 37: Prometheus - Installation and configuration
*   Day 38: Prometheus - Querying and alerting
*   Day 39: Grafana - Installation and configuration
*   Day 40: ELK Stack (Elasticsearch, Logstash, Kibana) - Overview and comparison

**Part 9: Cloud Platforms**

*   Day 41: Introduction to cloud platforms
*   Day 42: AWS - EC2, S3, and RDS
*   Day 43: AWS - IAM, VPC, and ELB
*   Day 44: Azure - Virtual Machines, Storage, and SQL Database
*   Day 45: Google Cloud Platform - Compute Engine, Storage, and Cloud SQL

**Part 10: DevOps Security**

*   Day 46: Introduction to DevOps security
*   Day 47: Security best practices for CI/CD pipelines
*   Day 48: Infrastructure and application security
*   Day 49: Container and Kubernetes security
*   Day 50: Cloud security and compliance

{{< /admonition >}}

---

## `git init`

`init` is the subcommand to initialize a new Git repository. Depending on where you run the command, it will create a new repository in the current working directory.

This creates a `.git` folder in the directory, and then you can use other Git commands and Git will track the changes.

In case you want to use `git init` in some other directory, you can pass the path to `git init` like `git init path/to/repository-working-directory`.

{{< admonition info "git init --bare" >}}
Generally, source code hosting sites like [GitHub](github.com) use `bare repository`. The repo in this case is initialized using `git init --bare`. To know more, check this [SO post](https://stackoverflow.com/questions/7861184/what-is-the-difference-between-git-init-and-git-init-bare).
{{< /admonition >}}

{{< admonition info "git init --separate-git-dir" >}}
By default, the `.git` folder stores any changes made in the directory where it exists, but we can actually use it to track a different working directory using the `--separate-git-dir` option, like `git init --separate-git-dir=/path/to/repos`.
{{< /admonition >}}

{{< admonition info "git init --initial-branch" >}}
You can also set the initial branch using the `--initial-branch` option, like `git init --initial-branch=my-initial-branch`.
{{< /admonition >}}

{{< admonition info "git init --initial-branch" >}}
There are other options like `--template`, which copies the default file and directory in the template folder, and `--shared`, which can be used to specify permissions.
{{< /admonition >}}

---

## `git add`
`add` is the subcommand to stage changes made to the working directory for the next commit.
Syntax: `git add [file or folder]`

To add all files in the current working directory, use the `git add .` command.

{{< admonition info "git add -i" >}}
There is also an interactive mode that you can access using `git add -i`, which presents you with a menu of options that allow you to:
- `status`: Show the current status of your working directory.
- `update`: Add modified files to the staging area.
- `revert`: Unstage files from the staging area.
- `add` untracked: Add untracked files to the staging area.
- `patch`: Interactively choose hunks of patch between the index and the work tree and add them to the index.
{{< /admonition >}}

{{< admonition info "git add -p" >}}
If your file has multiple changes and you want to stage only certain changes, you can use `git add -p <path/to/file>`. This gives you an interactive shell where you can selectively stage changes within a file.
{{< /admonition >}}

{{< admonition tip "git add :/" >}}
Sometimes you might be in a different folder than your root directory and you want to add all the files that are changed. In that case, you can use the `git add :/` command.
{{< /admonition >}}

---

## `git commit`
`commit` is the subcommand used to save changes to the local repository.
Syntax: `git commit -m "Commit Message"`

{{< admonition tip "git commit --allow-empty" >}}
Most of the time, you will see `git add .` followed by `git commit -m "commit message"`. There is a shorthand for this using `git commit -am "commit message"`.
{{< /admonition >}}

{{< admonition tip "git commit --allow-empty" >}}
Sometimes, your pull request pipeline may fail due to some initialization issues. If you don't have any way to re-trigger the pipeline using UI options in tools like GitHub Actions, Jenkins, or any other tool you are using, you can use `git commit --allow-empty -m "Empty commit to retrigger PR pipeline"`. This can also be used to mark certain phases of your project development, like `git commit --allow-empty -m "Empty commit to mark the end of phase 1"`.

Note that this creates clutter and should only be used if you really need it.
{{< /admonition >}}

{{< admonition tip "git commit --amend" >}}
Sometimes you mess up while writing a commit message and want to modify the last commit message. Or maybe you committed but forgot to add some changes which you intended to add before committing. You can use `git commit --amend` to modify the last commit message, including additional changes, instead of creating a new commit like `git commit --amend -m "New commit message"`.
{{< /admonition >}}

---

## `git status`
`git status` is the subcommand which displays the current status of a Git repository. The output shows which branch you're currently on, which files have been modified, which files are staged for commit, and which files are not tracked by Git.

Here are some scenarios you might see in git status.

### Scenario 1: No changes

```console
$ git status
On branch master
nothing to commit, working tree clean
```

### Scenario 2: Untacked files

```console
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        file.txt

nothing added to commit but untracked files present (use "git add" to track)
```

### Scenario 3: Changes to be committed

```console
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)

        modified:   file.txt
```

### Scenario 4: Changes not staged for commit

```console
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)

        modified:   file.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

### Scenario 5: Changes in branch ahead of remote

```console
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

{{< admonition tip "git status --short" >}}
`git status --short` let you display a compact version of `git status`.
{{< /admonition >}}

{{< admonition tip "git status --ignore-submodules" >}}
In case you have submodules and you don't want to display status about those, use `git status --ignore-submodules`.
{{< /admonition >}}

---

Here is a sequence digram to wrap it all up

{{< mermaid >}}
sequenceDiagram
    participant Workspace
    participant Index
    participant LocalRepo as Local Repository
    participant GitCommands as Git Commands

    GitCommands->>Workspace: git init
    Note over Workspace: Initialized as a Git repository
    GitCommands->>Workspace: Create or modify files
    GitCommands->>Workspace: git status
    Note over Workspace: Shows untracked/modified files

    GitCommands->>Index: git add <file>
    Note over Index: Stages changes for a file
    GitCommands->>Workspace: git status
    Note over Workspace: Shows staged changes

    GitCommands->>LocalRepo: git commit -m "Message"
    Note over LocalRepo: Commit staged changes
    GitCommands->>Workspace: git status
    Note over Workspace: Shows clean working tree
{{< /mermaid >}}

This diagram illustrates the following steps:

1.  `git init` initializes the workspace as a Git repository.
2.  Files are created or modified in the workspace.
3.  `git status` shows untracked or modified files in the workspace.
4.  `git add <file>` stages changes for a file, adding it to the index.
5.  `git status` shows staged changes in the workspace.
6.  `git commit -m "Message"` commits the staged changes to the local repository.
7.  `git status` shows a clean working tree, indicating that there are no changes to be committed.
