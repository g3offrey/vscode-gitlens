[![](https://vsmarketplacebadge.apphb.com/version-short/eamodio.gitlens.svg)](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
[![](https://vsmarketplacebadge.apphb.com/installs-short/eamodio.gitlens.svg)](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
[![](https://vsmarketplacebadge.apphb.com/rating-short/eamodio.gitlens.svg)](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
[![](https://img.shields.io/badge/vscode--dev--community-gitlens-blue.svg?logo=slack)](https://join.slack.com/t/vscode-dev-community/shared_invite/enQtMjIxOTgxNDE3NzM0LWU5M2ZiZDU1YjBlMzdlZjA2YjBjYzRhYTM5NTgzMTAxMjdiNWU0ZmQzYWI3MWU5N2Q1YjBiYmQ4MzY0NDE1MzY)

<p align="center">
  <br />
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/gitlens-header.png" alt="GitLens Logo" />
</p>

> GitLens **supercharges** the Git capabilities built into Visual Studio Code. It helps you to **visualize code authorship** at a glance via Git blame annotations and code lens, **seamlessly navigate and explore** Git repositories, **gain valuable insights** via powerful comparison commands, and so much more.

<br />

# GitLens

GitLens is a free, [open-source](https://github.com/eamodio/vscode-gitlens "Open GitLens on GitHub") extension for [Visual Studio Code](https://code.visualstudio.com) created by [Eric Amodio](http://amod.io "Learn more about Eric").

GitLens simply helps you understand code better. Quickly glimpse into whom, why, and when a line or code block was changed. Jump back through history to gain further insights as to how and why the code evolved. Explore the history and evolution of a codebase.

Here are just some of the features that GitLens provides,
 - a [*GitLens* explorer](#gitlens-explorer "Jump to the GitLens explorer") to navigate and explore repositories or file histories
 - an on-demand [*GitLens Results* view](#gitlens-results-view "Jump to the GitLens Results view") to explore commit searches, visualize comparisons between branches, tags, commits, and more
 - authorship [code lens](#code-lens "Jump to the Code Lens") showing the most recent commit and # of authors to the top of files and/or on code blocks
 - an unobtrusive [current line blame](#current-line-blame "Jump to the Current Line Blame") annotation at the end of the line
 - on-demand [gutter blame](#gutter-blame "Jump to the Gutter Blame") annotations, including a heatmap, for the whole file
 - detailed blame information accessible via [hovers](#hovers "Jump to the Hovers")
 - on-demand [recent changes](#recent-changes "Jump to the Recent Changes") annotations to highlight lines changed by the most recent commit
 - a [status bar blame](#status-bar-blame "Jump to the Status Bar Blame") annotation showing author and date for the current line
 - [commit search](#commit-search "Jump to the Commit Search") &mdash; by message, author, filename, commit id, or code changes
 - many powerful commands for exploring commits and histories, comparing and navigating revisions, stash access, repository status, etc
- and so much more

GitLens is powerful, feature rich, and also [highly customizable](#gitlens-settings "Jump to the GitLens settings docs") to meet your specific needs &mdash; find code lens intrusive or the current line blame annotation distracting &mdash; no problem, it is quick and easy to turn them off or change how they behave via the built-in *GitLens Settings* editor, a WYSIWYG editor covering many of GitLens' powerful settings. While for more advanced customizations, refer to the [GitLens settings docs](#gitlens-settings "Jump to the GitLens settings docs") and edit your vscode [user settings](https://code.visualstudio.com/docs/getstarted/settings "Open User settings").

<p align="center">
  <br />
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/gitlens-preview.gif" alt="GitLens Preview" />
  <br />
</p>

## Features

### GitLens Explorer
A [customizable](#gitlens-explorer-settings "Jump to the GitLens Explorer settings") explorer to navigate and explore repositories or file histories. The GitLens explorer provides two views (modes) &mdash; a Repository view and a History view.
- A toolbar provides *Search Commits*, *Switch to Repository View* or *Switch to History View*, and *Refresh* commands
  - Quickly switch between views using the *Switch to Repository View* or *Switch to History View* commands
  - A context menu provides *Automatic Layout*, *List Layout*, and *Tree Layout* commands

#### Repository view
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-gitlens-explorer-repository.png" alt="GitLens Explorer Repository view" />
</p>

The repository view provides a full Git repository explorer, which has the following features,

- **Repository Status**
  - Provides the name of the current branch, [optionally](#gitlens-explorer-settings "Jump to the GitLens explorer settings") its working tree status, and its upstream tracking branch and status (if available)
  - Provides indicator dots on the repository icon which denote the following:
    - *None* &mdash; up-to-date with the upstream
    - *Green* &mdash; ahead of the upstream
    - *Red* &mdash; behind the upstream
    - *Yellow* &mdash; both ahead of and behind the upstream
  - Provides additional upstream status nodes, if the current branch is tracking a remote branch and,
    - is behind the upstream &mdash; quickly see and explore the specific commits behind the upstream (i.e. commits that haven't been pulled)
    - is ahead of the upstream &mdash; quickly see and explore the specific commits ahead of the upstream (i.e. commits that haven't been pushed)
  - A context menu provides *Open Repository in Remote*, and *Refresh* commands
  - **Changed Files** &mdash; lists all the "working" changes
    - Expands to a file-based view of all changed files in the working tree ([optionally](#gitlens-explorer-settings "Jump to the GitLens explorer settings")) and/or all files in all commits ahead of the upstream

- **Branches** &mdash; lists the local branches
  - Indicates which branch is the current branch and [optionally](#gitlens-explorer-settings "Jump to the GitLens explorer settings") shows the remote tracking branch
  - A context menu provides *Open Branches in Remote*, and *Refresh* commands
  - Branches expand to show its revision (commit) history
    - Provides indicator dots on each branch icon which denote the following:
      - *None* &mdash; no upstream or up-to-date with the upstream
      - *Green* &mdash; ahead of the upstream
      - *Red* &mdash; behind the upstream
      - *Yellow* &mdash; both ahead of and behind the upstream
    - Context menus for each branch provide
      - *Open Branch in Remote* (if available), *Compare with Remote* (if available), *Compare with Index (HEAD)*, *Compare with Working Tree*, *Compare with Selected* (when available), *Compare Selected Ancestor with Working Tree* (when available), *Select for Compare*, *Open Directory Compare with Working Tree*, *Checkout Branch (via Terminal)*, *Merge Branch (via Terminal)*, *Rebase (Interactive) Branch (via Terminal)*, *Rebase (Interactive) Branch to Remote (via Terminal)*, *Squash Branch into Commit (via Terminal)*, *Create Branch (via Terminal)...*, *Delete Branch (via Terminal)*, *Create Tag (via Terminal)...*, and *Refresh* commands
    - Revisions (commits) expand to show the set of files changed, complete with status indicators for adds, changes, renames, and deletes
      - Context menus for each revision (commit) provide
        -  *Open Commit in Remote* (if available), *Open All Changes*, *Open All Changes with Working Tree*, *Open Files*, *Open Revisions*, *Copy Commit ID to Clipboard*, *Copy Commit Message to Clipboard*, *Show Commit Details*, *Compare with Index (HEAD)*, *Compare with Working Tree*, *Compare with Selected* (when available), *Select for Compare*, *Cherry Pick Commit (via Terminal)*, *Revert Commit (via Terminal)*, *Rebase to Commit (via Terminal)*, *Reset to Commit (via Terminal)*, *Create Branch (via Terminal)...*, *Create Tag (via Terminal)...*, and *Refresh* commands
      - Context menus for each changed file provide
        - *Open Changes*, *Open Changes with Working File*, *Open File*, *Open Revision*, *Open File in Remote*, *Open Revision in Remote*, *Apply Changes*, and *Show Commit File Details* commands

- **Remotes** &mdash; lists the remotes
  - Indicates the direction of the remote (fetch, push, both), remote service (if applicable), and repository path
  - A context menu provides a *Refresh* command
  - Remotes expands show its list of branches
    - Context menus for each remote provide
      - *Open Branches in Remote*, *Open Repository in Remote*, *Remove Remote (via Terminal)*, and *Refresh* commands
    - Branches expand to show its revision (commit) history
      - See the *Branches expand* section under **Branches** above for more details

- **Stashes** &mdash; lists the stashed changes
  - A context menu provides *Stash Changes*, and *Refresh* commands
  - Stashes expand to show the set of files stashed, complete with status indicators for adds, changes, renames, and deletes
    - Context menus for each stash provide
      - *Apply Stashed Changes* (confirmation required), *Delete Stashed Changes* (confirmation required), *Open All Changes*, *Open All Changes with Working Tree*, *Open Files*, *Open Revisions*, *Copy Commit Message to Clipboard*, *Compare with Index (HEAD)*, *Compare with Working Tree*, *Compare with Selected* (when available), *Select for Compare*, and *Refresh* commands
    - Context menus for each stashed file provide
      - *Apply Changes*, *Open Changes*, *Open Changes with Working File*, *Open File*, *Open Revision*, *Open File in Remote* (if available), and *Show File History* commands

- **Tags** &mdash; lists the tags
  - A context menu provides a *Refresh* command
  - Tags expand to show its revision (commit) history
    - Context menus for each tag provide
      - *Compare with Index (HEAD)*, *Compare with Working Tree*, *Compare with Selected*, *Select for Compare*, *Open Directory Compare with Working Tree*, *Delete Tag (via Terminal)*, and *Refresh* commands
    - Revisions (commits) expand to show the set of files changed, complete with status indicators for adds, changes, renames, and deletes
      - See the *Revisions (commits) expand* section under **Branches** above for more details

### History view
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-gitlens-explorer-history.png" alt="GitLens Explorer History view" />
</p>

The history view provides the revision history of the active file, which has the following features,
- Automatically updates to track the active editor
- A context menu provides *Open File*, *Open File in Remote* (if available), and *Refresh* commands
- Context menus for each revision (commit) provides
  - *Open Changes*, *Open Changes with Working File*, *Open File*, *Open Revision*, *Open File in Remote* (if available), *Open Revision in Remote* (if available), *Apply Changes*, and *Show Commit File Details* commands

---
### GitLens Results View
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-gitlens-results.png" alt="GitLens Results view" />
</p>

An on-demand, [customizable](#gitlens-results-view-settings "Jump to the GitLens Results view settings") view to explore commits, histories, and searches, or visualize comparisons between branches, tags, commits, and more
- A toolbar provides *Search Commits*, *Keep Results*, and *Refresh* commands
  - A context menu provides *Automatic Layout*, *List Layout*, *Tree Layout*, and *Close* commands

#### Explore
  - Provides a semi-persistent results view for exploring histories, commits, and searches
    - Accessible via the following commands
      - *Show Commit Search* command (`gitlens.showCommitSearch`)
      - *Show File History* command (`gitlens.showQuickFileHistory`)
      - *Show Commit Details* command (`gitlens.showQuickCommitDetails`)
    - Revisions (commits) expand show the set of files changed, complete with status indicators for adds, changes, renames, and deletes
      - Context menus for each revision (commit) provide
        -  *Open Commit in Remote* (if available), *Open All Changes*, *Open All Changes with Working Tree*, *Open Files*, *Open Revisions*, *Copy Commit ID to Clipboard*, *Copy Commit Message to Clipboard*, *Show Commit Details*, *Compare with Index (HEAD)*, *Compare with Working Tree*, *Compare with Selected* (when available), *Select for Compare*, *Cherry Pick Commit (via Terminal)*, *Revert Commit (via Terminal)*, *Rebase to Commit (via Terminal)*, *Reset to Commit (via Terminal)*, *Create Branch (via Terminal)...*, *Create Tag (via Terminal)...*, and *Refresh* commands
      - Context menus for each changed file provide
        - *Open Changes*, *Open Changes with Working File*, *Open File*, *Open Revision*, *Open File in Remote*, *Open Revision in Remote*, *Apply Changes*, and *Show Commit File Details* commands

#### Compare
  - Provides a semi-persistent results view for comparison operations
    - Accessible via the following commands
      - *Compare with Remote* command (`gitlens.explorers.compareWithRemote`)
      - *Compare with Index (HEAD)* command (`gitlens.explorers.compareWithHead`)
      - *Compare with Working Tree* command (`gitlens.explorers.compareWithWorking`)
      - *Compare with Selected* command (`gitlens.explorers.compareWithSelected`)
      - *Compare Selected Ancestor with Working Tree* command (`gitlens.explorers.compareSelectedAncestorWithWorking`)
    - A context menu provides *Clear Results*, *Open Directory Compare*, and *Refresh* commands

    - **Commits** &mdash; lists the commits between the compared revisions (branches or commits)
      - Revisions (commits) expand to show the set of files changed, complete with status indicators for adds, changes, renames, and deletes
        - See the *Revisions (commits) expand* section under **Explore** above for more details

    - **Changed Files** &mdash; lists the files changed between the compared revisions (branches or commits)
        - Expands to a file-based view of all changed files
           - Context menus for each changed file provide
             - *Open Changes*, *Open Changes with Working File*, *Open File*, *Open Revision*, *Open File in Remote*, *Open Revision in Remote*, *Apply Changes*, and *Show Commit File Details* commands

---
### Code Lens
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-code-lens.png" alt="Code Lens" />
</p>

- Adds Git authorship **code lens** to the top of the file and on code blocks ([optional](#code-lens-settings "Jump to the Code Lens settings"), on by default)

  - **Recent Change** &mdash; author and date of the most recent commit for the file or code block
    - Click the code lens to show a **commit file details quick pick menu** with commands for comparing, navigating and exploring commits, and more (by [default](#code-lens-settings "Jump to the Code Lens settings"))
  - **Authors** &mdash; number of authors of the file or code block and the most prominent author (if there is more than one)
    - Click the code lens to toggle the file Git blame annotations on and off of the whole file (by [default](#code-lens-settings "Jump to the Code Lens settings"))
    - Will be hidden if the author of the most recent commit is also the only author of the file or block, to avoid duplicate information and reduce visual noise

  - Provides [customizable](#code-lens-settings "Jump to the Code Lens settings") click behavior for each code lens &mdash; choose between one of the following
    - Toggle file blame annotations on and off
    - Compare the commit with the previous commit
    - Show a quick pick menu with details and commands for the commit
    - Show a quick pick menu with file details and commands for the commit
    - Show a quick pick menu with the commit history of the file
    - Show a quick pick menu with the commit history of the current branch

- Adds a *Toggle Git Code Lens* command (`gitlens.toggleCodeLens`) with a shortcut of `shift+alt+b` to toggle the code lens on and off

---
### Current Line Blame
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-current-line-blame.png" alt="Current Line Blame" />
</p>

- Adds an unobtrusive, [customizable](#current-line-blame-settings "Jump to the Current Line Blame settings"), and [themable](#themable-colors "Jump to the Themable Colors"), **blame annotation** at the end of the current line
  - Contains the author, date, and message of the current line's most recent commit (by [default](#current-line-blame-settings "Jump to the Current Line Blame settings"))
  - Adds a *Show Line Blame Annotations* command (`gitlens.showLineBlame`)
  - Adds a *Toggle Line Blame Annotations* command (`gitlens.toggleLineBlame`) to toggle the blame annotation on and off

---
### Gutter Blame
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-gutter-blame.png" alt="Gutter Blame">
</p>

- Adds on-demand, [customizable](#gutter-blame-settings "Jump to the Gutter Blame settings"), and [themable](#themable-colors "Jump to the Themable Colors"), **gutter blame annotations** for the whole file
  - Contains the commit message and date, by [default](#gutter-blame-settings "Jump to the Gutter Blame settings")
  - Adds a **heatmap** (age) indicator on right edge (by [default](#gutter-blame-settings "Jump to the Gutter Blame settings")) of the gutter to provide an easy, at-a-glance way to tell the age of a line ([optional](#gutter-blame-settings "Jump to the Gutter Blame settings"), on by default)
    - Indicator ranges from bright yellow (newer) to dark brown (older)
  - Adds a *Show File Blame Annotations* command (`gitlens.showFileBlame`)
  - Adds a *Toggle File Blame Annotations* command (`gitlens.toggleFileBlame`) with a shortcut of `alt+b` to toggle the blame annotations on and off
  - Press `Escape` to turn off the annotations

---
### Gutter Heatmap
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-heatmap.png" alt="Gutter Heatmap" />
</p>

- Adds an on-demand **heatmap** to the edge of the gutter to show the relative age of a line
  - Indicator ranges from bright yellow (newer) to dark brown (older)
  - Adds *Toggle File Heatmap Annotations* command (`gitlens.toggleFileHeatmap`) to toggle the heatmap on and off
  - Press `Escape` to turn off the annotations

---
### Hovers
#### Current Line Hovers
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-hovers-current-line.png" alt="Current Line Hovers" />
</p>

- Adds [customizable](#hover-settings "Jump to the Hover settings") Git blame hovers accessible over the current line

##### Details Hover
  <p align="center">
    <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-hovers-current-line-details.png" alt="Current Line Details Hover" />
  </p>

- Adds a **details hover** annotation to the current line to show more commit details ([optional](#hover-settings "Jump to the Hover settings"), on by default)
  - Provides a **quick-access command bar** with *Open Changes*, *Blame Previous Revision*, *Open in Remote*, and *Show More Actions* command buttons
  - Click the commit id to execute the *Show Commit Details* command (`gitlens.showQuickCommitDetails`)

##### Changes (diff) Hover
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-hovers-current-line-changes.png" alt="Current Line Changes (diff) Hover" />
</p>

- Adds a **changes (diff) hover** annotation to the current line to show the line's previous version ([optional](#hover-settings "Jump to the Hover settings"), on by default)
  - Click the **Changes** to execute the *Compare File Revisions* command (`gitlens.diffWith`)
  - Click the current and previous commit ids to execute the *Show Commit Details* command (`gitlens.showQuickCommitDetails`)

#### Annotation Hovers
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-hovers-annotations.png" alt="Annotation Hovers" />
</p>

- Adds [customizable](#hover-settings "Jump to the Hover settings") Git blame hovers accessible when annotating

##### Details Hover
  <p align="center">
    <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-hovers-annotations-details.png" alt="Annotations Details Hover" />
  </p>

- Adds a **details hover** annotation to each line while annotating to show more commit details ([optional](#hover-settings "Jump to the Hover settings"), on by default)
  - Provides a **quick-access command bar** with *Open Changes*, *Blame Previous Revision*, *Open in Remote*, and *Show More Actions* command buttons
  - Click the commit id to execute the *Show Commit Details* command (`gitlens.showQuickCommitDetails`)

##### Changes (diff) Hover
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-hovers-annotations-changes.png" alt="Annotations Changes (diff) Hover" />
</p>

- Adds a **changes (diff) hover** annotation to each line while annotating to show the line's previous version ([optional](#hover-settings "Jump to the Hover settings"), on by default)
  - Click the **Changes** to execute the *Compare File Revisions* command (`gitlens.diffWith`)
  - Click the current and previous commit ids to execute the *Show Commit Details* command (`gitlens.showQuickCommitDetails`)

---
### Recent Changes
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-recent-changes.png" alt="Recent Changes" />
</p>

- Adds an on-demand, [customizable](#recent-changes-settings "Jump to the Recent Changes settings") and [themable](#themable-colors "Jump to the Themable Colors"), **recent changes annotation** to highlight lines changed by the most recent commit
  - Adds *Toggle Recent File Changes Annotations* command (`gitlens.toggleFileRecentChanges`) to toggle the recent changes annotations on and off
  - Press `Escape` to turn off the annotations

---
### Status Bar Blame
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-status-bar.png" alt="Status Bar Blame" />
</p>

- Adds a [customizable](#status-bar-settings "Jump to the Status Bar Blame settings") **Git blame annotation** about the current line to the **status bar** ([optional](#status-bar-settings "Jump to the Status Bar Blame settings"), on by default)

  - Contains the commit author and date (by [default](#status-bar-settings "Jump to the Status Bar Blame settings"))
  - Click the status bar item to show a **commit details quick pick menu** with commands for comparing, navigating and exploring commits, and more (by [default](#status-bar-settings "Jump to the Status Bar Blame settings"))

  - Provides [customizable](#status-bar-settings "Jump to the Status Bar Blame settings") click behavior &mdash; choose between one of the following
    - Toggle file blame annotations on and off
    - Toggle code lens on and off
    - Compare the line commit with the previous commit
    - Compare the line commit with the working tree
    - Show a quick pick menu with details and commands for the commit (default)
    - Show a quick pick menu with file details and commands for the commit
    - Show a quick pick menu with the commit history of the file
    - Show a quick pick menu with the commit history of the current branch

---
### Commit Search
- Adds a *Search Commits* command (`gitlens.showCommitSearch`) with a shortcut of `alt+/` to search for commits by message, author, file(s), commit id, or code changes
  - Use `<message>` to search for commits with messages that match `<message>` &mdash; See [Git docs](https://git-scm.com/docs/git-log#git-log---grepltpatterngt "Open Git docs")
  - Use `@<pattern>` to search for commits with authors that match `<pattern>` &mdash; See [Git docs](https://git-scm.com/docs/git-log#git-log---authorltpatterngt "Open Git docs")
  - Use `:<pattern>` to search for commits with file names that match `<pattern>` &mdash; See [Git docs](https://git-scm.com/docs/git-log "Open Git docs")
  - Use `#<sha>` to search for a commit with id of `<sha>` &mdash; See [Git docs](https://git-scm.com/docs/git-log "Open Git docs")
  - Use `~<pattern>` to search for commits with differences whose patch text contains added/removed lines that match `<pattern>` &mdash; See [Git docs](https://git-scm.com/docs/git-log#git-log--Gltregexgt "Open Git docs")
  - Use `=<string>` to search for commits with differences that change the number of occurrences of the specified string (i.e. addition/deletion) in a file &mdash; See [Git docs](https://git-scm.com/docs/git-log#git-log--Sltstringgt "Open Git docs")
  - Provides a *Show in Results* option to show the search results in the **GitLens Results** view

---
### Navigate and Explore

- Adds a *Show Last Opened Quick Pick* command (`gitlens.showLastQuickPick`) with a shortcut of `alt+-` to quickly get back to where you were when the last GitLens quick pick menu closed

- Adds commands to open files, commits, branches, and the repository in the supported remote services, **BitBucket, GitHub, GitLab, and Visual Studio Team Services** or a [**user-defined** remote services](#custom-remotes-settings "Jump to Custom Remotes settings") &mdash; only available if a Git upstream service is configured in the repository
  - Also supports [remote services with custom domains](#custom-remotes-settings "Jump to Custom Remotes settings"), such as **BitBucket, Bitbucket Server (previously called Stash), GitHub, GitHub Enterprise, GitLab**
  - *Open Branches in Remote* command (`gitlens.openBranchesInRemote`) &mdash; opens the branches in the supported remote service
  - *Open Branch in Remote* command (`gitlens.openBranchInRemote`) &mdash; opens the current branch commits in the supported remote service
  - *Open Commit in Remote* command (`gitlens.openCommitInRemote`) &mdash; opens the commit revision of the active line in the supported remote service
  - *Open File in Remote* command (`gitlens.openFileInRemote`) &mdash; opens the active file/revision in the supported remote service
  - *Open Repository in Remote* command (`gitlens.openRepoInRemote`) &mdash; opens the repository in the supported remote service

#### Branch History
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-menu-branch-history.png" alt="Branch History Quick Pick Menu" />
</p>

- Adds a *Show Current Branch History* command (`gitlens.showQuickRepoHistory`) with a shortcut of `shift+alt+h` to show a paged **branch history quick pick menu** of the current branch for exploring its commit history
  - Provides entries to *Show Commit Search* and *Open Branch in \<remote-service\>* when available
  - Navigate back to the previous quick pick menu via `alt+left arrow`, if available
  - Navigate pages via `alt+,` and `alt+.` to go backward and forward respectively

- Adds a *Show Branch History* command (`gitlens.showQuickBranchHistory`) to show a paged **branch history quick pick menu** of the selected branch for exploring its commit history
  - Provides the same features as *Show Current Branch History* above

#### File History
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-menu-file-history.png" alt="File History Quick Pick Menu" />
</p>

- Adds a *Show File History* command (`gitlens.showQuickFileHistory`) to show a paged **file history quick pick menu** of the active file for exploring its commit history
  - Provides additional entries to *Show in Results*, *Show Branch History*, and *Open File in \<remote-service\>* when available
  - Navigate back to the previous quick pick menu via `alt+left arrow`, if available
  - Navigate pages via `alt+,` and `alt+.` to go backward and forward respectively

#### Commit Details
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-menu-commit-details.png" alt="Commit Details Quick Pick Menu" />
</p>

- Adds a *Show Commit Details* command (`gitlens.showQuickCommitDetails`) to show a **commit details quick pick menu** of the most recent commit of the active file
  - Quickly see the set of files changed in the commit, complete with status indicators for adds, changes, renames, and deletes
  - Provides additional entries to *Show in Results*, *Open Commit in \<remote-service\>* when available, *Open Files*, *Open Revisions*, *Open Directory Compare with Previous Revision*, *Open Directory Compare with Working Tree*, *Copy Commit ID to Clipboard*, *Copy Commit Message to Clipboard*
  - Navigate back to the previous quick pick menu via `alt+left arrow`, if available
  - Use the `alt+right arrow` shortcut on an entry to execute it without closing the quick pick menu, if possible &mdash; commands that open windows outside of VS Code will still close the quick pick menu unless [`"gitlens.advanced.quickPick.closeOnFocusOut": false`](#advanced-settings "Jump to Advanced settings") is set
  - Use the `alt+right arrow` shortcut on a file entry in the `Changed Files` section to preview the comparison of the current revision with the previous one

<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-menu-commit-file-details.png" alt="Commit File Details Quick Pick Menu" />
</p>

- Adds a *Show Commit File Details* command (`gitlens.showQuickCommitFileDetails`) with a shortcut of `alt+c` to show a **file commit details quick pick menu** of the most recent commit of the active file
  - Provides entries to *Open Changes*, *Open Changes with Working File*, *Open File*, *Open Revision*, *Open File in \<remote-service\>* when available, *Open Revision in \<remote-service\>* when available, *Copy Commit ID to Clipboard*, *Copy Commit Message to Clipboard*, *Show Commit Details*, *Show File History*, and *Show Previous File History*
  - Navigate back to the previous quick pick menu via `alt+left arrow`, if available
  - Use the `alt+right arrow` shortcut on an entry to execute it without closing the quick pick menu, if possible &mdash; commands that open windows outside of VS Code will still close the quick pick menu unless [`"gitlens.advanced.quickPick.closeOnFocusOut": false`](#advanced-settings "Jump to Advanced settings") is set

#### Repository Status
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-menu-repo-status.png" alt="Repository Status Quick Pick Menu" />
</p>

- Adds a *Show Repository Status* command (`gitlens.showQuickRepoStatus`) with a shortcut of `alt+s` to show a **repository status quick pick menu** for visualizing the current repository status
  - Quickly see upstream status (if an Git upstream is configured) &mdash; complete with ahead and behind information
    - If you are ahead of the upstream, an entry will be shown with the number of commits ahead. Choosing it will show a limited **branch history quick pick menu** containing just the commits ahead of the upstream
    - If you are behind the upstream, an entry will be shown with the number of commits behind. Choosing it will show a limited **branch history quick pick menu** containing just the commits behind the upstream
  - Quickly see all working changes, both staged and unstaged, complete with status indicators for adds, changes, renames, and deletes
  - Provides entries to *Show Stashed Changes*, *Open Changed Files*, and *Close Unchanged Files*
  - Use the `alt+right arrow` shortcut on an entry to execute it without closing the quick pick menu, if possible &mdash; commands that open windows outside of VS Code will still close the quick pick menu unless [`"gitlens.advanced.quickPick.closeOnFocusOut": false`](#advanced-settings "Jump to Advanced settings") is set
  - Use the `alt+right arrow` shortcut on a file entry in the `Staged Files` or `Unstaged Files` sections to preview the comparison of the working file with the previous revision

#### Stashes
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-menu-stash-list.png" alt="Stashed Changes Quick Pick Menu" />
</p>

- Adds a *Show Stashed Changes* command (`gitlens.showQuickStashList`) to show a **stashed changes quick pick menu** for exploring your repository stash history
  - Provides additional entries to *Stash Changes*
  - Navigate back to the previous quick pick menu via `alt+left arrow`, if available

- Adds a *Stash Changes* command (`gitlens.stashSave`) to save any working tree changes to the stash &mdash; can optionally provide a stash message
  - Also adds the command to the Source Control items context menu to stash an individual or group of files, works with multi-select too!

#### Stash Details
<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/develop/images/ss-menu-stash-details.png" alt="Stash Details Quick Pick Menu" />
</p>

  - Stashed changes show a **stash details quick pick menu** which is very similar to the **commit details quick pick menu** above
    - Quickly see the set of files changed in the stash, complete with status indicators for adds, changes, renames, and deletes
    - Provides additional entries to *Apply Stashed Changes* (requires confirmation), *Delete Stashed Changes* (requires confirmation), *Open Files*, *Open Revisions*, *Open Directory Compare with Previous Revision*, *Open Directory Compare with Working Tree*, *Copy Commit Message to Clipboard*
    - Navigate back to the previous quick pick menu via `alt+left arrow`, if available
    - Use the `alt+right arrow` shortcut on an entry to execute it without closing the quick pick menu, if possible &mdash; commands that open windows outside of VS Code will still close the quick pick menu unless [`"gitlens.advanced.quickPick.closeOnFocusOut": false`](#advanced-settings "Jump to Advanced settings") is set
    - Use the `alt+right arrow` shortcut on a file entry in the `Changed Files` section to  preview the comparison of the current revision with the previous one

- Adds a *Apply Stashed Changes* command (`gitlens.stashApply`) to chose a stash entry to apply to the working tree from a quick pick menu

---
### Powerful Comparison Tools

- Effortlessly navigate between comparisons via the `alt+,` and `alt+.` shortcut keys to go back and forth through a file's revisions

- Provides easy access to the following comparison commands via the `Command Palette` as well as in context via the many provided quick pick menus

- Adds a *Directory Compare Working Tree with...* command (`gitlens.diffDirectory`) to open the configured Git difftool to compare the working tree with the selected branch or tag

- Adds a *Compare File with Branch or Tag...* command (`gitlens.diffWithBranch`) to compare the active file with the same file on the selected branch or tag

- Adds a *Compare File with Next Revision* command (`gitlens.diffWithNext`) with a shortcut of `alt+.` to compare the active file/diff with the next commit revision

- Adds a *Compare File with Previous Revision* command (`gitlens.diffWithPrevious`) with a shortcut of `alt+,` to compare the active file/diff with the previous commit revision

- Adds a *Compare Line Revision with Previous* command (`gitlens.diffLineWithPrevious`) with a shortcut of `shift+alt+,` to compare the active file/diff with the previous line commit revision

- Adds a *Compare File with Revision...* command (`gitlens.diffWithRevision`) to compare the active file with the selected revision of the same file

- Adds a *Compare File with Working Revision* command (`gitlens.diffWithWorking`) with a shortcut of `shift+alt+w` to compare the most recent commit revision of the active file/diff with the working tree

- Adds a *Compare Line Revision with Working File* command (`gitlens.diffLineWithWorking`) with a shortcut of `alt+w` to compare the commit revision of the active line with the working tree

---
### And More

- Adds a *Copy Commit ID to Clipboard* command (`gitlens.copyShaToClipboard`) to copy the commit id (sha) of the active line to the clipboard or from the most recent commit to the current branch, if there is no active editor

- Adds a *Copy Commit Message to Clipboard* command (`gitlens.copyMessageToClipboard`) to copy the commit message of the active line to the clipboard or from the most recent commit to the current branch, if there is no active editor

- Adds a *Open Working File"* command (`gitlens.openWorkingFile`) to open the working file for the active file revision

- Adds a *Open Revision...* command (`gitlens.openFileRevision`) to open the selected revision for the active file

- Adds a *Open Changes (with difftool)* command (`gitlens.externalDiff`) to the source control group and source control resource context menus to open the changes of a file or set of files with the configured git difftool

- Adds a *Open All Changes (with difftool)* command (`gitlens.externalDiffAll`) to open all working changes with the configured git difftool
  - Also adds the command to the Source Control group context menu

- Adds a *Open Changed Files* command (`gitlens.openChangedFiles`) to open any files with working tree changes

- Adds a *Close Unchanged Files* command (`gitlens.closeUnchangedFiles`) to close any files without working tree changes

---
## GitLens Settings

GitLens is highly customizable and provides many configuration settings to allow the personalization of almost all features.

### General Settings

|Name | Description
|-----|------------
|`gitlens.defaultDateFormat`|Specifies how absolute dates will be formatted by default<br />See https://momentjs.com/docs/#/displaying/format/ for valid formats
|`gitlens.defaultDateStyle`|Specifies how dates will be displayed by default
|`gitlens.defaultGravatarsStyle`|Specifies the style of the gravatar default (fallback) images<br />`identicon` - a geometric pattern<br />`mm` - (mystery-man) a simple, cartoon-style silhouetted outline of a person (does not vary by email hash)<br />`monsterid` - a monster with different colors, faces, etc<br />`retro` - 8-bit arcade-style pixelated faces<br />`robohash` - a robot with different colors, faces, etc<br />`wavatar` - faces with differing features and backgrounds
|`gitlens.insiders`|Opts into the insiders channel &mdash; provides access to upcoming features
|`gitlens.keymap`|Specifies the keymap to use for GitLens shortcut keys<br />`standard` - adds a standard set of shortcut keys<br />`chorded` - adds a chorded set of shortcut keys that all start with `Ctrl+Shift+G` (`⌥⌘G` on macOS)<br />`none` - no shortcut keys will be added
|`gitlens.outputLevel`|Specifies how much (if any) output will be sent to the GitLens output channel
|`gitlens.showWhatsNewAfterUpgrades`|Specifies whether or not to show What's New after upgrading to new feature releases

### GitLens Explorer Settings

See also [Explorer Settings](#explorer-settings "Jump to the Explorer settings")

|Name | Description
|-----|------------
|`gitlens.gitExplorer.autoRefresh`|Specifies whether or not to automatically refresh the **GitLens** view when the repository or the file system changes
|`gitlens.gitExplorer.branches.layout`| Specifies how the **Branches** view will display branches<br />`list` - display all branches<br />`tree` - organize branch as folder if branch name contains slashes "/"<br />`mix-tree` - display branch folders along with normal branch alphabetically
|`gitlens.gitExplorer.enabled`|Specifies whether or not to show the **GitLens** view"
|`gitlens.gitExplorer.files.compact`|Specifies whether or not to compact (flatten) unnecessary file nesting in the **GitLens** view<br />Only applies when displaying files as a `tree` or `auto`
|`gitlens.gitExplorer.files.layout`|Specifies how the **GitLens** view will display files<br /> `auto` - automatically switches between displaying files as a `tree` or `list` based on the `gitlens.gitExplorer.files.threshold` setting and the number of files at each nesting level<br /> `list` - displays files as a list<br /> `tree` - displays files as a tree
|`gitlens.gitExplorer.files.threshold`|Specifies when to switch between displaying files as a `tree` or `list` based on the number of files in a nesting level in the **GitLens** view<br />Only applies when displaying files as `auto`
|`gitlens.gitExplorer.includeWorkingTree`|Specifies whether or not to include working tree files inside the `Repository Status` node of the **GitLens** view
|`gitlens.gitExplorer.showTrackingBranch`|Specifies whether or not to show the tracking branch when displaying local branches in the **GitLens** view"
|`gitlens.gitExplorer.view`|Specifies the starting view (mode) of the **GitLens** view<br /> `auto` - shows the last selected view, defaults to `repository`<br />`history` - shows the commit history of the active file<br />`repository` - shows a repository explorer"

### GitLens Results View Settings

See also [Explorer Settings](#explorer-settings "Jump to the Explorer settings")

|Name | Description
|-----|------------
|`gitlens.resultsExplorer.files.compact`|Specifies whether or not to compact (flatten) unnecessary file nesting in the **GitLens Results** view<br />Only applies when displaying files as a `tree` or `auto`
|`gitlens.resultsExplorer.files.layout`|Specifies how the **GitLens Results** view will display files<br /> `auto` - automatically switches between displaying files as a `tree` or `list` based on the `gitlens.resultsExplorer.files.threshold` setting and the number of files at each nesting level<br /> `list` - displays files as a list<br /> `tree` - displays files as a tree
|`gitlens.resultsExplorer.files.threshold`|Specifies when to switch between displaying files as a `tree` or `list` based on the number of files in a nesting level in the **GitLens Results** view<br />Only applies when displaying files as `auto`

### Explorer Settings

|Name | Description
|-----|------------
|`gitlens.explorers.avatars`|Specifies whether or not to show avatar images instead of commit (or status) icons in the **GitLens** and **GitLens Results** views
|`gitlens.explorers.commitFileFormat`|Specifies the format of a committed file in the **GitLens** and **GitLens Results** views<br />Available tokens<br /> ${directory} - directory name<br /> ${file} - file name<br /> ${filePath} - formatted file name and path<br /> ${path} - full file path
|`gitlens.explorers.commitFormat`|Specifies the format of committed changes in the **GitLens** and **GitLens Results** views<br />Available tokens<br /> ${id} - commit id<br /> ${author} - commit author<br /> ${message} - commit message<br /> ${ago} - relative commit date (e.g. 1 day ago)<br /> ${date} - formatted commit date (format specified by `gitlens.statusBar.dateFormat`)<br /> ${authorAgo} - commit author, relative commit date<br />See https://github.com/eamodio/vscode-gitlens/wiki/Advanced-Formatting for advanced formatting
|`gitlens.explorers.stashFileFormat`|Specifies the format of a stashed file in the **GitLens** and **GitLens Results** views<br />Available tokens<br /> ${directory} - directory name<br /> ${file} - file name<br /> ${filePath} - formatted file name and path<br /> ${path} - full file path
|`gitlens.explorers.stashFormat`|Specifies the format of stashed changes in the **GitLens** and **GitLens Results** views<br />Available tokens<br /> ${id} - commit id<br /> ${author} - commit author<br /> ${message} - commit message<br /> ${ago} - relative commit date (e.g. 1 day ago)<br /> ${date} - formatted commit date (format specified by `gitlens.statusBar.dateFormat`)<br /> ${authorAgo} - commit author, relative commit date<br />See https://github.com/eamodio/vscode-gitlens/wiki/Advanced-Formatting for advanced formatting
|`gitlens.explorers.statusFileFormat`|Specifies the format of the status of a working or committed file in the **GitLens** and **GitLens Results** views<br />Available tokens<br /> ${directory} - directory name<br /> ${file} - file name<br /> ${filePath} - formatted file name and path<br /> ${path} - full file path<br />${working} - optional indicator if the file is uncommitted

### Code Lens Settings

|Name | Description
|-----|------------
|`gitlens.codeLens.authors.command`|Specifies the command to be executed when the `authors` code lens is clicked<br />`gitlens.toggleFileBlame` - toggles file blame annotations<br />`gitlens.diffWithPrevious` - compares the current committed file with the previous commit<br />`gitlens.showQuickCommitDetails` - shows a commit details quick pick<br />`gitlens.showQuickCommitFileDetails` - shows a commit file details quick pick<br />`gitlens.showQuickFileHistory` - shows a file history quick pick<br />`gitlens.showQuickRepoHistory` - shows a branch history quick pick
|`gitlens.codeLens.authors.enabled`|Specifies whether or not to show an `authors` code lens showing number of authors of the file or code block and the most prominent author (if there is more than one)
|`gitlens.codeLens.enabled`|Specifies whether or not to provide any Git code lens, by default<br />Use the *Toggle Git Code Lens* command (`gitlens.toggleCodeLens`) to toggle the Git code lens on and off for the current window
|`gitlens.codeLens.recentChange.command`|Specifies the command to be executed when the `recent change` code lens is clicked<br />`gitlens.toggleFileBlame` - toggles file blame annotations<br />`gitlens.diffWithPrevious` - compares the current committed file with the previous commit<br />`gitlens.showQuickCommitDetails` - shows a commit details quick pick<br />`gitlens.showQuickCommitFileDetails` - shows a commit file details quick pick<br />`gitlens.showQuickFileHistory` - shows a file history quick pick<br />`gitlens.showQuickRepoHistory` - shows a branch history quick pick
|`gitlens.codeLens.recentChange.enabled`|Specifies whether or not to show a `recent change` code lens showing the author and date of the most recent commit for the file or code block
|`gitlens.codeLens.scopes`|Specifies where Git code lens will be shown in the document<br />`document` - adds code lens at the top of the document<br />`containers` - adds code lens at the start of container-like symbols (modules, classes, interfaces, etc)<br />`blocks` - adds code lens at the start of block-like symbols (functions, methods, etc) lines
|`gitlens.codeLens.scopesByLanguage`|Specifies where Git code lens will be shown in the document for the specified languages
|`gitlens.codeLens.symbolScopes`|Specifies a set of document symbols where Git code lens will or will not be shown in the document<br />Prefix with `!` to not show Git code lens for the symbol<br />Must be a member of `SymbolKind`

#### Current Line Blame Settings

|Name | Description
|-----|------------
|`gitlens.currentLine.dateFormat`|Specifies how to format absolute dates (using the `${date}` token) for the current line blame annotations<br />See https://momentjs.com/docs/#/displaying/format/ for valid formats
|`gitlens.currentLine.enabled`|Specifies whether or not to provide a blame annotation for the current line, by default<br />Use the *Toggle Line Blame Annotations* command (`gitlens.toggleLineBlame`) to toggle the annotations on and off for the current window
|`gitlens.currentLine.format`|Specifies the format of the current line blame annotation<br />Available tokens<br />`${id}` - commit id<br />`${author}` - commit author<br />`${message}` - commit message<br />`${ago}` - relative commit date (e.g. 1 day ago)<br />`${date}` - formatted commit date (format specified by `gitlens.annotations.line.trailing.dateFormat`)<br />`${authorAgo}` - commit author, relative commit date<br />See https://github.com/eamodio/vscode-gitlens/wiki/Advanced-Formatting for advanced formatting

### Gutter Blame Settings

|Name | Description
|-----|------------
|`gitlens.blame.avatars`|Specifies whether or not to show avatar images in the gutter blame annotations
|`gitlens.blame.compact`|Specifies whether or not to compact (deduplicate) matching adjacent gutter blame annotations
|`gitlens.blame.dateFormat`|Specifies how to format absolute dates (using the `${date}` token) in gutter blame annotations<br />See https://momentjs.com/docs/#/displaying/format/ for valid formats
|`gitlens.blame.format`|Specifies the format of the gutter blame annotations<br />Available tokens<br />`${id}` - commit id<br />`${author}` - commit author<br />`${message}` - commit message<br />`${ago}` - relative commit date (e.g. 1 day ago)<br />`${date}` - formatted commit date (format specified by `gitlens.blame.dateFormat`)<br />`${authorAgo}` - commit author, relative commit date<br />See https://github.com/eamodio/vscode-gitlens/wiki/Advanced-Formatting for advanced formatting
|`gitlens.blame.heatmap.enabled`|Specifies whether or not to provide a heatmap indicator in the gutter blame annotations
|`gitlens.blame.heatmap.location`|Specifies where the heatmap indicators will be shown in the gutter blame annotations<br />`left` - adds a heatmap indicator on the left edge of the gutter blame annotations<br />`right` - adds a heatmap indicator on the right edge of the gutter blame annotations
|`gitlens.blame.highlight.enabled`|Specifies whether or not to highlight lines associated with the current line
|`gitlens.blame.highlight.locations`|Specifies where the associated line highlights will be shown<br />`gutter` - adds a gutter glyph<br />`line` - adds a full-line highlight background color<br />`overviewRuler` - adds a decoration to the overviewRuler (scroll bar)
|`gitlens.blame.ignoreWhitespace`|Specifies whether or not to ignore whitespace when comparing revisions during blame operations
|`gitlens.blame.separateLines`|Specifies whether or not gutter blame annotations will have line separators

### Hover Settings

|Name | Description
|-----|------------
|`gitlens.hovers.annotations.changes`|Specifies whether or not to provide a changes (diff) hover for all lines when showing blame annotations
|`gitlens.hovers.annotations.details`|Specifies whether or not to provide a commit details hover for all lines when showing blame annotations
|`gitlens.hovers.annotations.enabled`|Specifies whether or not to provide any hovers when showing blame annotations
|`gitlens.hovers.annotations.over`|Specifies when to trigger hovers when showing blame annotations<br /> `annotation` - only shown when hovering over the line annotation<br /> `line` - shown when hovering anywhere over the line
|`gitlens.hovers.currentLine.changes`|Specifies whether or not to provide a changes (diff) hover for the current line
|`gitlens.hovers.currentLine.details`|Specifies whether or not to provide a commit details hover for the current line
|`gitlens.hovers.currentLine.enabled`|Specifies whether or not to provide any hovers for the current line
|`gitlens.hovers.currentLine.over`|Specifies when to trigger hovers for the current line<br /> `annotation` - only shown when hovering over the line annotation<br /> `line` - shown when hovering anywhere over the line
|`gitlens.hovers.enabled`|Specifies whether or not to provide any hovers

### Recent Changes Settings

|Name | Description
|-----|------------
|`gitlens.recentChanges.highlight.locations`|Specifies where the highlights of the recently changed lines will be shown<br />`gutter` - adds a gutter glyph<br />`line` - adds a full-line highlight background color<br />`overviewRuler` - adds a decoration to the overviewRuler (scroll bar)

### Status Bar Settings

|Name | Description
|-----|------------
|`gitlens.statusBar.alignment`|Specifies the blame alignment in the status bar<br />`left` - align to the left,  `right` - align to the right
|`gitlens.statusBar.command`|Specifies the command to be executed when the blame status bar item is clicked<br />`gitlens.toggleFileBlame` - toggles file blame annotations<br />`gitlens.diffWithPrevious` - compares the current line commit with the previous<br />`gitlens.diffWithWorking` - compares the current line commit with the working tree<br />`gitlens.toggleCodeLens` - toggles Git code lens<br />`gitlens.showQuickCommitDetails` - shows a commit details quick pick<br />`gitlens.showQuickCommitFileDetails` - shows a commit file details quick pick<br />`gitlens.showQuickFileHistory` - shows a file history quick pick<br />`gitlens.showQuickRepoHistory` - shows a branch history quick pick
|`gitlens.statusBar.dateFormat`|Specifies the date format of absolute dates shown in the blame information on the status bar<br />See https://momentjs.com/docs/#/displaying/format/ for valid formats
|`gitlens.statusBar.enabled`|Specifies whether or not to provide blame information on the status bar
|`gitlens.statusBar.format`|Specifies the format of the blame information on the status bar<br />Available tokens<br />`${id}` - commit id<br />`${author}` - commit author<br />`${message}` - commit message<br />`${ago}` - relative commit date (e.g. 1 day ago)<br />`${date}` - formatted commit date (format specified by `gitlens.statusBar.dateFormat`)<br />See https://github.com/eamodio/vscode-gitlens/wiki/Advanced-Formatting for advanced formatting

### Advanced Settings

|Name | Description
|-----|------------
|`gitlens.advanced.blame.delayAfterEdit`|Specifies the time (in milliseconds) to wait before re-blaming an unsaved document after an edit. Use 0 to specify an infinite wait
|`gitlens.advanced.blame.sizeThresholdAfterEdit`|Specifies the maximum document size (in lines) allowed to be re-blamed after an edit while still unsaved. Use 0 to specify no maximum
|`gitlens.advanced.caching.enabled`|Specifies whether git output will be cached &mdash; changing the default is not recommended
|`gitlens.advanced.git`|Specifies the git path to use
|`gitlens.advanced.maxListItems`|Specifies the maximum number of items to show in a list. Use 0 to specify no maximum
|`gitlens.advanced.menus`|Specifies which commands will be added to which menus
|`gitlens.advanced.messages`|Specifies which messages should be suppressed
|`gitlens.advanced.quickPick.closeOnFocusOut`|Specifies whether or not to close QuickPick menus when focus is lost
|`gitlens.advanced.repositorySearchDepth`|Specifies how many folders deep to search for repositories
|`gitlens.advanced.telemetry.enabled`|Specifies whether or not to enable GitLens telemetry (even if enabled still abides by the overall `telemetry.enableTelemetry` setting

#### Custom Remotes Settings

|Name | Description
|-----|------------
|`gitlens.remotes`|Specifies user-defined remote (code-hosting) services or custom domains for built-in remote services<br /><br />Example:<br />```"gitlens.remotes": [{ "domain": "git.corporate-url.com", "type": "GitHub" }]```<br /><br />Example:<br />```"gitlens.remotes": [{ ```<br />&nbsp;&nbsp;&nbsp;&nbsp;```"domain": "git.corporate-url.com",```<br />&nbsp;&nbsp;&nbsp;&nbsp;```"type": "Custom",```<br />&nbsp;&nbsp;&nbsp;&nbsp;```"name": "My Company", ```<br />&nbsp;&nbsp;&nbsp;&nbsp;```"protocol": "https",```<br />&nbsp;&nbsp;&nbsp;&nbsp;```"urls": {```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"repository": "https://git.corporate-url.com/${repo}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"branches": "https://git.corporate-url.com/${repo}/branches",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"branch": "https://git.corporate-url.com/${repo}/commits/${branch}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"commit": "https://git.corporate-url.com/${repo}/commit/${id}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"file": "https://git.corporate-url.com/${repo}?path=${file}${line}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"fileInBranch": "https://git.corporate-url.com/${repo}/blob/${branch}/${file}${line}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"fileInCommit": "https://git.corporate-url.com/${repo}/blob/${id}/${file}${line}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"fileLine": "#L${line}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"fileRange": "#L${start}-L${end}"```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```}```<br />&nbsp;&nbsp;&nbsp;&nbsp;```}]```<br /><br />Example:<br />```"gitlens.remotes": [{ ```<br />&nbsp;&nbsp;&nbsp;&nbsp;```"domain": "git.corporate-url.com",```<br />&nbsp;&nbsp;&nbsp;&nbsp;```"type": "Custom",```<br />&nbsp;&nbsp;&nbsp;&nbsp;```"name": "My Company", ```<br />&nbsp;&nbsp;&nbsp;&nbsp;```"protocol": "https",```<br />&nbsp;&nbsp;&nbsp;&nbsp;```"urls": {```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"repository": "https://git.corporate-url.com/projects/${repoBase}/repos/${repoPath}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"branches": "https://git.corporate-url.com/projects/${repoBase}/repos/${repoPath}/branches",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"branch": "https://git.corporate-url.com/projects/${repoBase}/repos/${repoPath}/commits/${branch}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"commit": "https://git.corporate-url.com/projects/${repoBase}/repos/${repoPath}/commit/${id}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"file": "https://git.corporate-url.com/projects/${repoBase}/repos/${repoPath}?path=${file}${line}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"fileInBranch": "https://git.corporate-url.com/projects/${repoBase}/repos/${repoPath}/blob/${branch}/${file}${line}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"fileInCommit": "https://git.corporate-url.com/projects/${repoBase}/repos/${repoPath}/blob/${id}/${file}${line}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"fileLine": "#L${line}",```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```"fileRange": "#L${start}-L${end}"```<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;```}```<br />&nbsp;&nbsp;&nbsp;&nbsp;```}]```

#### Strings Settings

|Name | Description
|-----|------------
|`gitlens.strings.codeLens.unsavedChanges.recentChangeAndAuthors`|Specifies the string to be shown in place of both the `recent change` and `authors` code lens when there are unsaved changes
|`gitlens.strings.codeLens.unsavedChanges.recentChangeOnly`|Specifies the string to be shown in place of the `recent change` code lens when there are unsaved changes
|`gitlens.strings.codeLens.unsavedChanges.authorsOnly`|Specifies the string to be shown in place of the `authors` code lens when there are unsaved changes

---
## Themable Colors

GitLens defines a set of themable colors which can be provided by vscode themes or directly by the user using [`workbench.colorCustomization`](https://code.visualstudio.com/docs/getstarted/themes#_customize-a-color-theme).

|Name | Description
|-----|------------
|`gitlens.gutterBackgroundColor`|Specifies the background color of the gutter blame annotations
|`gitlens.gutterForegroundColor`|Specifies the foreground color of the gutter blame annotations
|`gitlens.gutterUncommittedForegroundColor`|Specifies the foreground color of an uncommitted line in the gutter blame annotations
|`gitlens.trailingLineBackgroundColor`|Specifies the background color of the trailing blame annotation
|`gitlens.trailingLineForegroundColor`|Specifies the foreground color of the trailing blame annotation
|`gitlens.lineHighlightBackgroundColor`|Specifies the background color of the associated line highlights in blame annotations
|`gitlens.lineHighlightOverviewRulerColor`|Specifies the overview ruler color of the associated line highlights in blame annotations

---
## Insiders

Add [`"gitlens.insiders": true`](#general-settings "Jump to GitLens settings") to your settings to join the insiders channel and get early access to upcoming features. Be aware that because this provides early access expect there to be issues.

---
## Known Issues

- If the `Copy to * clipboard` commands don't work on Linux &mdash; `xclip` needs to be installed. You can install it via `sudo apt-get install xclip`

---
## Contributors

A big thanks to the people that have contributed to this project:

- Amanda Cameron ([@AmandaCameron](https://github.com/AmandaCameron)) &mdash; [contributions](https://github.com/eamodio/vscode-gitlens/commits?author=AmandaCameron))
- Helmut Januschka ([@hjanuschka](https://github.com/hjanuschka)) &mdash; [contributions](https://github.com/eamodio/vscode-gitlens/commits?author=hjanuschka))
- Chris Kaczor ([@ckaczor](https://github.com/ckaczor)) &mdash; [contributions](https://github.com/eamodio/vscode-gitlens/commits?author=ckaczor))
- Peng Lyu ([@rebornix](https://github.com/rebornix)) &mdash; [contributions](https://github.com/eamodio/vscode-gitlens/commits?author=rebornix))
- Aurelio Ogliari ([@nobitagit](https://github.com/nobitagit)) &mdash; [contributions](https://github.com/eamodio/vscode-gitlens/commits?author=nobitagit)
- Johannes Rieken ([@jrieken](https://github.com/jrieken)) &mdash; [contributions](https://github.com/eamodio/vscode-gitlens/commits?author=jrieken))
- Zack Schuster ([@zackschuster](https://github.com/zackschuster)) &mdash; [contributions](https://github.com/eamodio/vscode-gitlens/commits?author=zackschuster)
- SpaceEEC ([@SpaceEEC](https://github.com/SpaceEEC)) &mdash; [contributions](https://github.com/eamodio/vscode-gitlens/commits?author=SpaceEEC)
- Alexey Vasyukov ([@notmedia](https://github.com/notmedia)) &mdash; [contributions](https://github.com/eamodio/vscode-gitlens/commits?author=notmedia))

Also special thanks to the people that have provided support, testing, brainstorming, etc:

- Brian Canzanella ([@bcanzanella](https://github.com/bcanzanella))
- Matt King ([@KattMingMing](https://github.com/KattMingMing))

And of course the awesome [vscode](https://github.com/Microsoft/vscode/graphs/contributors) team!
