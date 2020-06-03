# Git and File Line Endings on Windows

LF only in all Cordova Repositories (execption `cordova-windows`)

usually `git config --global core.autocrlf true` is a great solution: CRLF on Windows working copy (checkout), but LF everywhere else. See advice from GitHub; https://help.github.com/en/articles/dealing-with-line-endings
breaks down when using working copy to create a release with e.g. `npm pack` or similar.

Solution: `.gitattributes` with `* text eol=lf`. Tells git to always use LF, also on Windows.
Caution: Files created locally with CRLF stay that way locally.

## Find problematic files

- `grep -Pnr --include=* --exclude-dir={\.git,node_modules} '\r$' .` ([via](https://stackoverflow.com/a/33281752/252627))
- `find . -not -type d -exec file "{}" ";" | grep CRLF` ([via](https://stackoverflow.com/a/73969/252627))
  
## Fix automatically

Commit everything, delete everything but `.git`, `git reset --hard`.

## Fix manually

- Manually in editor of choice
- `dos2unix`

---

Additional input via https://gist.github.com/ajdruff/16427061a41ca8c08c05992a6c74f59e#file-fix-git-line-endings-L31
