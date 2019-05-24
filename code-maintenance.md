# Code Maintenance

Steps we regularly take to make sure our code is in a good state.

## Licences

[Background information](http://www.apache.org/legal/src-headers.html)
TODO

### Licence Headers

Ensure license headers are present everywhere:

```bash
coho audit-license-headers -r android | less
```

TODO Properly handle this: "Ensure license headers are present everywhere. For reference, see this background. Expect some noise in the output, for example some files from test fixtures will show up."

### Dependency Licences

Ensure all dependencies and subdependencies have Apache-compatible licenses:

```bash
coho check-license -r android
```

## Dependencies

### `npm outdated --depth=0`

- Variant 1: Pin the outdated dependency in `dependencies` of `package.json`, create issue to update.
- Variant 2: Update the dependency by creating a Pull Request with the changes.

### `npm audit`

TODO How are results handled?

(Might require running `npm i --package-lock-only` before, and deleting `package-lock.json` afterwards)

### Pinned dependencies

TODO
