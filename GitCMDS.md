# Git commands

```
# Remove file from git
git rm file1.txt
git rm --cached file1.txt    ; Remved from git but not from filesystem
```

```
# Git commit
git commit -m "Removed the file test"
```

```
# Delete local branch
git branch -d branch_name ; deletes local branch if pushed
git branch -D branch_name ; deletes the branch
```

```
# Delete remote branch
git push origin --delete  branch_name
```

```
# Clean untracked files
git clean -n
# To see while files will be deleted
```

```
# Delete untracked files
git clean -f
```

```
# Remove untracked directory
git clean -fd
```

```
# Create git ignore files
touch .gitignore
```
