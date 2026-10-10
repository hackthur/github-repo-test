# github-repo-test



## Commands

```bash
❯ git status
❯ git add <filename>
❯ git blame <filename>
❯ git hash-object <filename>
❯ git hash-object file-1.txt
❯ git branch -a
❯ git remote show origin 
❯ git tag --sort=-version:refname
❯ git log --oneline --decorate --graph --all
```




## Making a blob object

```bash
❯  echo "test content"
test content
❯ echo "test content" | git hash-object --stdin
d670460b4b4aece5915caf5c68d12f560a9fe3e4
❯ git cat-file -p d670460b4b4aece5915caf5c68d12f560a9fe3e4
test content
❯ git cat-file -t d670460b4b4aece5915caf5c68d12f560a9fe3e4
blob

```
