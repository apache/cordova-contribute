# Create a minimal reproduction repository or sample

When you report an issue or bug for any of the Apache Cordova packages, it is very helpful to create and include and link to a reproduction repository or sample.

## Why?

After you create your GitHub issue, someone from the Apache Cordova team will look at it and then has to decide if your issue is an actual bug or maybe "just" some problem in your individual code or how you use one of our libraries. 

They will have to evaluate the described problem and confirm that it exists. They will only be able to do so if you supplied [enough and the correct information in your issue](TODO). This can be very time consuming and cumbersome. Even then it can be tough, because it is almost impossible to include all your environment information and code in an issue.

If you create a reproduction repository, the maintainer will have _all_ the same information you have.

As a side effect, it also forces you to reproduce the bug outside of your individual project and with a minimal set of libraries and plugins included. Very often this will tell you a lot of additional information about the bug itself, that would be hard to come by in your usual project. 

Maybe you even figure out it is not an actual bug at all, but an unrelated problem that only manifests in your project because of other reason.

## How?

1. Execute the command `cordova create` to create a new project locally
1. Create a public Git repository on e.g. GitHub or Bitbucket and initialize a repository with that remote in your newly created Cordova project
1. Commit that clean and empty project to your Git repository
1. Then add the platforms and/or plugins needed to reproduce the problem
1. Commit the changes in the project again and include the exact commands you executed in the commit message
1. Then change the code of the sample project so it triggers your problem
1. Finally commit the reproduction code for your bug to Git and post the repository to your issue

The Cordova maintainer then can check out your Git repository, and just run the commands you described to actually see and experience the bug.

The repository later can also be a "test" to confirm the problem is actually resolved in an updated version of whatever library is faulty.
