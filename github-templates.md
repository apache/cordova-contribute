# GitHub Templates

GitHub supports templates that are pre-populated into the description input field of a newly opened Issues and Pull Requests. Apache Cordova uses both options.

## Issue Templates

The job of an issue template is to make sure, the creator includes all necessary information in an issue they open. It can also supply information to the reporter like text or links that are relevant before opening an issue.

Apache Cordova uses [GitHub's multiple issues template functionality](https://help.github.com/articles/about-issue-and-pull-request-templates/), which
lets users choose what type of issue they want to create:

Note: You can "test" and preview these issue templates by [creating an issue](/issues) in this repository.

### Bug Report

Collect all necessary information to understand if this is an actual bug or just a user problem. The information collected should enable the Apache Cordova community to reproduce and resolve the problem.

See [`.github/ISSUE_TEMPLATE/BUG_REPORT.md`](.github/ISSUE_TEMPLATE/BUG_REPORT.md) for our current bug report template.

### Feature Request

What new feature is being requested and what problem does it solve?

See [`.github/ISSUE_TEMPLATE/FEATURE_REQUEST.md`](.github/ISSUE_TEMPLATE/FEATURE_REQUEST.md) for our current feature request template.

### Support Question

People having problems with using one of Apache Cordova's components tend to also create issues. Apache Cordova unfortunately does not have the community to handle that volume of issues. Because of that, this template mainly refer people to the proper, more suited support channels:

- Stack Overflow
- Slack
- Framework channels (like e.g. Ionic Forum)

**Note that Apache Cordova will close support questions if they are submitted to the repository anyway.**

See [`.github/ISSUE_TEMPLATE/SUPPORT_QUESTION.md`](.github/ISSUE_TEMPLATE/SUPPORT_QUESTION.md) for our current support question template.

### Fallback

Users can still ignore the specific issue templates by going to the `/issues/new` URL directly or use the "Don’t see your issue here? Open a regular issue." link below the template selection. This template provides the fallback for this case.

See [`.github/ISSUE_TEMPLATE.md`](.github/ISSUE_TEMPLATE.md) for our current fallback issues template.

## Pull Request Template

Similar to an [Issue Template](#issue-template), the Pull Request template ensures that new Pull Requests include all necessary information. It is also used to nudge contributors to run tests, write documentation etc.

See [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) for our current pull request template.

## Distribute GitHub Templates to all repositories

Distributing these templates manually would take quite some time. For that reason @janpio wrote a small script that takes care of the process:

1. Check out both this repository [`cordova-contribute`](https://github.com/apache/cordova-contribute) and [`cordova-coho`](https://github.com/apache/cordova-coho) in the same folder.
1. In `cordova-coho` run `npm install` and `npm link`.
1. Go one level up, create a folder (e.g. `coho Checkouts`) and go into that folder.
1. Run `coho repo-update -g -r all` to check out "all" Cordova repositories.
1. Remove the folders of repositories you don't want to distribute the templates to.
1. Check out any other Apache Cordova repositories that `coho` might have missed.
1. Create a file `run.rb` with the following content:
    ```ruby
    folders = Dir.glob('*').select {|f| File.directory? f}
    @source = "../cordova-contribute/.github"
    require 'fileutils'
    folders.each do |folder| 
        FileUtils.copy_entry @source, "#{folder}/.github"
        Dir.chdir(folder)
        `git add .github`
        `git commit -m "Add or update GitHub pull request and issue template"`
        `git push origin`
        Dir.chdir("..")
    end
    ```
    This gets all folders, iterates through them and copies the templates from `../cordova-contribute/.github` to `.github` in each folder, then adds the new files via git and commits and pushes the changes.
1. Execute the script with `ruby run.rb` and wait until it is finished.
1. Manually confirm that everything went well.