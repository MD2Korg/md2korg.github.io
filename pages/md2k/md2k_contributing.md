---
title: Contributing Guidelines
keywords: documentation theme, jekyll, technical writers, help authoring tools, hat replacements
tags: [getting_started]
summary: "TODO"
sidebar: md2k_sidebar
permalink: contributing.html
folder: md2k
---


# Contributing guidelines
Thank you for your interest in helping us with the MD2K software platforms.  We always welcome new contributions in any form including:

- Bug reports regarding the software, documentation, website, etc...
- Documentation improvements, tutorials, examples
- Code patches and new features

## Getting started
Please join and explore our [mailing list](https://groups.google.com/forum/#!forum/md2k-dev).  This is all our discussions occur regarding the MD2K software projects.

## What can I help with
We try to keep all open issues for MD2K software on [JIRA](https://md2korg.atlassian.net/issues/?filter=-4) but please ask on the mailing list before starting work on any issues.

## Code contribution process
While contributing to any MD2K software modules, you will encounter a variety of coding styles, frameworks, and principles.  The most important thing to do is to communicate with the development teams throughout the whole process.

## Before you start the work
Most issues should be brought up in the [mailing list](https://groups.google.com/forum/#!forum/md2k-dev). After discussion, a JIRA issue will be created

## Creating the contribution as a GitHub Pull request
MD2K utilizes [GitHub's Pull Requests](https://help.github.com/articles/using-pull-requests/) as the primary mechanism to accept changes: fork the specific MD2K software repository, make your changes, and send a pull request.

1. Fork a MD2K repository
1. Create a branch
1. Make changes on your local machine
1. Merge the master branch into your branch
1. Push commits into your remote forked repository
1. Send pull request to the MD2K team
1. Participate in the code review process on GitHub


### Fork repository
Goto the appropriate [GitHub repository](https://github.com/MD2Korg/) and click the "Fork" button to have your own copy.  Clone this onto your local machine:
```
$ git clone https://github.com/[YOUR_GITHUB_ID]/[REPOSITORY_NAME].github
```

Add a remote upstream to your repository:
```
$ git remote add upstream https://github.com/MD2Korg/[REPOSITORY_NAME]
```

Configure your name and email if necessary:
```
$ git config user.name "FirstName LastName"
$ git config user.email email@domain.com
```

### Create a branch to work with
Ensure that the issue you are going to solve is allocated and assigned in the [JIRA](https://md2korg.atlassian.net/issues/?filter=-4) issue tracker.  Create a branch to address the issue and the name should reference the JIRA issue, e.g., MD2K-[ISSUE NUMBER].

### Make local changes
Write code and make commits and usual.  Code should contain appropriate licensing in headers and ensure that existing tests pass.

### Merge the master branch into your branch
Prior to sending a pull request, you should ensure that your branch contain the latest changes.  Run the following:
```
$ git fetch upstream
$ git checkout [YOUR_BRANCH] # Skip the step if you are already on your branch
$ git merge upstream/master
```

Please resolve all conflicts that arise and test your merged code so that it does not break anything.

As a courtesy to the merger, you should rebase to master and squash all the commits from your PR into one:
```
# rebase
$ git rebase -i upstream/master
```

In the rebase process, make sure that the contribution is squashed to a single commit. From the list of commits, "pick" the commit in the first line (the oldest), and "squash" the commits in the remaining lines:
```
pick   7387a49 Comment for first commit
squash 3371411 Comment for second commit
squash 9bf956d Comment for third commit
```

For more information, please see [chapter 3](http://www.git-scm.com/book/en/v2/Git-Branching-Rebasing) and [chapter 4](http://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) of the [Git Book](http://www.git-scm.com/book/en/v2).

During this process, git will allow you to edit the commit message for the final, squashed commit and it will serve as the description of the pull request.  A common template for the commit message is:
```
[MD2K-JIRA_ISSUE_NUMBER] Title of the JIRA issue

Description of issues addressed:
  * Something
  * Something else
  * ...
```

### Push commits into your remote repository
Almost done, push your commits to GitHub.
```
$ git push origin head
```

### Send a pull request
Please read [this](https://help.github.com/articles/using-pull-requests/) for more information about pull requests.  Go to your repository on the GitHub website and click the button "Compare & Pull request".  You will be given an option to choose which branches to compare and merge, choose the base as the MD2Korg repository master branch and the head as [your_alias]:[branch_name].  Feel free to edit the description with more details.

Please update the JIRA issue with a link to the Pull Request to alert the MD2K team to start a code review process.

### Code review
We utilize the GitHub commenting system on Pull Requests for the code review and once this process is complete, the MD2K team will squash and merge your contribution into the MD2K codebase.  Thank you for your effort and support.
