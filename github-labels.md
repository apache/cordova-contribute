# GitHub Labels

Apache Cordova uses [Github Issues](github-issues.md) for issue tracking and [GitHub Pull Requests](github-pull-requests.md) for code changes and contributions. Issues and Pull Requests use [labels](https://help.github.com/articles/about-labels/) for organization and categorization.

Cordova does _not_ use labels for version, milestone or release tracking. [GitHub Milestones](github-milestones.md) are used for that.

## Apache Cordova GitHub Labels

The following defines the label names, label description and label color in use:

### Default labels

The [default labels](https://help.github.com/articles/about-labels/#using-default-labels) created with new repositories offer a good baseline:

- ![#f03c15](https://placehold.it/20/d73a4a/000000?text=+) `bug`: Something isn't working
- ![#cfd3d7](https://placehold.it/20/cfd3d7/000000?text=+) `duplicate`: This issue or pull request already exists
- ![#a2eeef](https://placehold.it/20/a2eeef/000000?text=+) `enhancement`: ~~New feature or request~~ Changes to existing code
- ![#7057ff](https://placehold.it/20/7057ff/000000?text=+) `good first issue`: Good for newcomers
- ![#008672](https://placehold.it/20/008672/000000?text=+) `help wanted`: Extra attention is needed
- ![#e4e669](https://placehold.it/20/e4e669/000000?text=+) `invalid`: This doesn't seem right
- ![#d876e3](https://placehold.it/20/d876e3/000000?text=+) `question`: Further information is requested - to be replaced by (or renamed to) `info-needed` (see below)
- ![#ffffff](https://placehold.it/20/ffffff/000000?text=+) `wontfix`: This will not be worked on

The label names `good first issue` and `help wanted` have [special meaning](https://help.github.com/articles/helping-new-contributors-find-your-project-with-labels/) on GitHub.

#### Changes to default labels

The list above has some ~~strike through~~ text. These are our changes to the default labels, so they don't clash with out custom labels below.

### Custom labels

- ![#d876e3](https://placehold.it/20/d876e3/000000?text=+) `info-needed`: Further information is requested
- ![#0e8a16](https://placehold.it/20/0e8a16/000000?text=+) `feature`: New functionality that requires new code
- ![#1d76db](https://placehold.it/20/1d76db/000000?text=+) `discussion`: Creator is open to suggestions or wants to discuss how something should be implemented
- ![#ccc](https://placehold.it/20/ccc/000000?text=+) `support`: Support questions that want to understand how something works, need help debugging their individual problem etc. are closed and tagged with this label.

#### Plugin repositories

For plugin repositories it makes sense to categorize Issues - e.g. a bug report or feature request - or Pull Requests by its platform:

- ![#c5def5](https://placehold.it/20/c5def5/000000?text=+) `platform: ios`
- ![#c2e0c6](https://placehold.it/20/c2e0c6/000000?text=+) `platform: android`
- ![#fef2c0](https://placehold.it/20/fef2c0/000000?text=+) `platform: browser`
- ![#d4c5f9](https://placehold.it/20/d4c5f9/000000?text=+) `platform: windows`

<!--
### Possible future labels

A collection of labels that might be useful for Cordova in the future, with e.g. some automation in place:

```
waiting-for-information: Requested more information from user and waiting for reply.
confirmed: To indicate a bug has been replicated and a PR fixing the problem should be created.
has-pr: Issues that already have a PR that is waiting to get reviewed/merged/released.
work-in-progress: Someone is currently working on this Pull Request.

triage
needs investigation
needs info
needs reply 
cannot reproduce 

status: auto-closed
status: waiting-for-reply
status: needs-attention
status: on-hold
status: blocked

status: included-in-next-release
status: released

type: code-improvement
type: documentation

effort: low
effort: moderate
effort: high

priority: low
priority: high

P4: nice to have
P3: important
P2: required
P1: urgent
P0: critical
```

-->

## Distribute GitHub Labels to multiple repositories

As the labels above are not distributed to all Cordova repositories automatically yet, they have to be created on demand. Contributors of Apache Cordova are able to just create any label they need manually.

TODO
<!--
Pseudocode:
Go through all repositories
  Go through list of label definitions
    If label already exists
      Update description and color
      # This is important as the color and descriptions mentioned above are pretty new, so most of Cordova's repositories are configured with an older color set and without descriptions.
    If label does not exist
      Create label with description and color
  If labels exist that are not part of label definitions
    Output details for manual handling
      - name, description, color
      - number of issues

Existing Alternatives:
- http://www.dorukdestan.com/github-label-manager/ 
  - https://medium.com/@dtinth/how-to-copy-github-labels-from-one-project-to-another-1857adc73e0f
  - terrible security practices as basic auth is used
- https://github.com/HewlettPackard/yoda/blob/master/docs/MANUAL.md#label-manager
  https://hewlettpackard.github.io/yoda/yoda-label-manager.html
- https://gist.github.com/symm/ba69f2b715558c61b1a2 
  - Could be used for a simple PHP script
- https://github.com/BlueAcornInc/github-label-manager
  uses https://github.com/jasonbellamy/git-label
- https://github.com/himynameisdave/git-labelmaker
  uses https://github.com/jasonbellamy/git-label

-->
