# GitHub Labels

Apache Cordova uses [Github Issues](github-issues.md) for issue tracking and [GitHub Pull Requests](github-pull-requests.md) for code changes and contributions. Issues and Pull Requests use [labels](https://help.github.com/articles/about-labels/) for organization and categorization.

Cordova does _not_ use labels for version, milestone or release tracking. [GitHub Milestones](github-milestones.md) are used for that.

## Apache Cordova GitHub Labels

The following defines the label names, label description and label color in use:

### Default labels

The [default labels](https://help.github.com/articles/about-labels/#using-default-labels) created with new repositories offer a good baseline:

- <div style="background-color:#d73a4a; padding:3px 8px; border-radius: 3px; display:inline;">bug</div>: Something isn't working
- <div style="background-color:#cfd3d7; padding:3px 8px; border-radius: 3px; display:inline;">duplicate</div>: This issue or pull request already exists
- <div style="background-color:#a2eeef; padding:3px 8px; border-radius: 3px; display:inline;">enhancement</div>: ~~New feature or request~~ Changes to existing code
- <div style="background-color:#7057ff; padding:3px 8px; border-radius: 3px; display:inline;">good first issue</div>: Good for newcomers
- <div style="background-color:#008672; padding:3px 8px; border-radius: 3px; display:inline;">help wanted</div>: Extra attention is needed
- <div style="background-color:#e4e669; padding:3px 8px; border-radius: 3px; display:inline;">invalid</div>: This doesn't seem right
- <div style="background-color:#d876e3; padding:3px 8px; border-radius: 3px; display:inline;">question</div>: Further information is requested
- <div style="background-color:#ffffff; padding:3px 8px; border-radius: 3px; display:inline;">wontfix</div>: This will not be worked on

The label names `good first issue` and `help wanted` have [special meaning](https://help.github.com/articles/helping-new-contributors-find-your-project-with-labels/) on GitHub.

#### Changes to default labels

The list above has some ~~strike through~~ text. These are our changes to the default labels, so they don't clash with out custom labels below.

### Custom labels

- <div style="background-color:#0e8a16; padding:3px 8px; border-radius: 3px; display:inline;">feature</div>: New functionality that requires new code
- <div style="background-color:#1d76db; padding:3px 8px; border-radius: 3px; display:inline;">discussion</div>: Creator is open to suggestions or wants to discuss how something should be implemented
- <div style="background-color:#ccc; padding:3px 8px; border-radius: 3px; display:inline;">support</div>: Support questions that want to understand how something works, need help debugging their individual problem etc. are closed and tagged with this label.

#### Plugin repositories

For plugin repositories it makes sense to categorize Issues - e.g. a bug report or feature request - or Pull Requests by its platform:

- <div style="background-color:#c5def5; padding:3px 8px; border-radius: 3px; display:inline;">platform: ios</div>
- <div style="background-color:#c2e0c6; padding:3px 8px; border-radius: 3px; display:inline;">platform: android</div>
- <div style="background-color:#fef2c0; padding:3px 8px; border-radius: 3px; display:inline;">platform: browser</div>
- <div style="background-color:#d4c5f9; padding:3px 8px; border-radius: 3px; display:inline;">platform: windows</div>

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
