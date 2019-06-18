# Release Process for Cordova Core Plugins with `cort`

## Before

- `cort apache:buyinmail`
- Check out `master` branch of plugin
- `cort identify` to understand
- Manual: Create or check out release branch if needed

## Release

- `cort update-release-notes`
- Manual: Curate release notes
- `cort version:undev`
- `cort release:commit`
- `cort release:votetag` (TODO, currently `release:tag`)
- `cort apache:archive`
- `cort apache:upload`
- `cort apache:votemail`

### Enable further development

- `cort version:bump`
- `cort version:dev`
- `cort release:preparecommit`
- `cort release:push`

## Finish

### If vote succeeds

- `cort apache:move`
- `cort release:tag`
- `cort release:publish`
- Manual: Cherry pick changes from release branch to `master`
- `cort apache:releasemail`

### If vote fails

- TODO
