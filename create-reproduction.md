# Create a Minimal Reproduction Repository or Sample

When reporting an issue or bug, for any of the Apache Cordova packages, it is helpful to create and include a link to a reproduction repository or sample.

## Why?

When an Apache Cordova team member reviews a GitHub issue, they need to be able to identify if the issue is either a bug, a problem originating from the users' source code, or how the user is using one of our libraries.

For an efficient evaluation, it is imported to supply a detail report with [enough and correct information](TODO). Gathering the information can be cumbersome and even tough as there are many aspects to the working environment and code.

By creating a reproduction repository, a maintainer should have _all_ of the same information.

The goal of a reproduce repository is to be able to replicate the bug in a minimalist project containing only the necessary libraries and plugins. Often, being able to replicate the bug outside of the usual project will lead to explaining more information.

By creating the minimalist project to reproduce the issue, it may be possible to discover that it's not a bug, but something unrelated and only manifests in the main project for other reasons.

## How?

1. Execute the command `cordova create` to create a new project locally.
1. Initialize Git on the new Cordova project and set the remote repository to a public repository from any public accessible Git service provider. Example: GitHub, Bitbucket, GitLab, etc
1. Commit the clean and empty project to the public remote Git repository.
1. Add the platform(s) and/or plugin(s) needed to reproduce the problem.
1. Commit the changes in the project again and include the exact commands executed in the commit message.
1. Change the code, of the sample project in which trigger the problem.
1. Commit the reproduction code for the bug to Git and post the repository to the issue ticket.

A Cordova maintainer will then be able to check out the Git repository and follow the step commands, as described, to reproduce and experience the bug.

Later, the repository can be used as a "test" to confirm if the problem has been resolved in a future update in regards to the library that was faulty.
