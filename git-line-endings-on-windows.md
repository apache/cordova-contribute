# Git and File Line Endings on Windows

LF only in all Cordova Repositories (execption `cordova-windows`)

usually `git config --global core.autocrlf true` is a great solution: CRLF on Windows working copy (checkout), but LF everywhere else.
breaks down when using working copy to create a release with e.g. `npm pack` or similar.

Solution: `.gitattributes` with `* text eol=lf`. Tells git to always use LF, also on Windows.
Caution: Files created locally with CRLF stay that way locally.

Fix automatically:
Commit everything, delete everything but `.git`, `git reset`.

Fix manually:
Find files (and lines) that still have CRLF:
`grep -Pnr --include=* --exclude-dir=\.git '\r$' .`
`find . -not -type d -exec file "{}" ";" | grep CRLF` (Git bash on Windows)
Convert: `dos2unix`
