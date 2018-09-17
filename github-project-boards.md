# GitHub Project Boards

Apache Cordova uses GitHub Project Boards to manage and track both issues and pull requests.

## Release Management

- [Next Release Planning and Tracking](https://github.com/orgs/apache/projects/2?fullscreen=true)

TODO description

## Issue Management

TODO

## Pull Requests Management

For Pull Requests we track their "review and merge progress" on project boards:

- [Platform Pull Requests](https://github.com/orgs/apache/projects/7?fullscreen=true)
- [Tooling Pull Requests](https://github.com/orgs/apache/projects/8?fullscreen=true)
- [Plugin Pull Requests (1)](https://github.com/orgs/apache/projects/9?fullscreen=true): camera, file, inappbrowser, media splashscreen
- [Plugin Pull Requests (2)](https://github.com/orgs/apache/projects/10?fullscreen=true): dialogs, geolocation, media-capture, statusbar, whitelist

### Process

#### Columns

- Pull Requests start in the "New PR / Untriaged" column (added manually by using the "Add Card" functionality) 
- They can then be sorted by a maintainer into columns according to their "review" readiness ("Blocked: Work in Progress", "Blocked: Conflict", "Blocked: Tests failing" or "Ready for Review").  
- On review, merge, close etc. they are moved to other columns by automation ("Pending Approval", "Approved, waiting for Merge", "Merged, waiting for Release", "Closed/Abandoned").  
- After release they are manually moved to the "Released" column.

#### Labels

[GitHub Labels](github-labels.md) for platform (`platform: ios`, `platform: android`) and type (`bug`, `feature`, `enhancement`) are used to categorize pull requests.
