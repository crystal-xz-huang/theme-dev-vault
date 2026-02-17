
## Git Add

The `git add` command adds new or changed files in your working directory to the Git staging area.

- `git add <file>`  to add a specific file
- `git add .`   to add all the changed files

### Unstaging Files – Undo Git Add

```shell
git reset <file/path> 
# or
git restore --staged <file/path>
```

**Stage all files**

Stages all changes (new, modified, and deleted files) within the **current directory** and its subdirectories. 

```shell
git add . 
```

> The `.` adds the entire directory recursively, including files whose names begin with a dot. 

Stages all changes in the **entire repository**, regardless of your current directory. This includes new files, modified files, and deleted files in the current directory *and* in higher directories that still belong to the same git repository.

```shell
git add -A # (or git add --all)
```

Stages modified and deleted files only, **NOT new, untracked files**.

```shell
git add -u # (or git add --update)
```

| Command      | New files | Modified files | Deleted files | Hidden files | Current directory | Higher directories |
| ------------ | --------- | -------------- | ------------- | ------------ | ----------------- | ------------------ |
| `git add -A` | ✅         | ✅              | ✅             | ✅            | ✅                 | ✅                  |
| `git add .`  | ✅         | ✅              | ✅             | ✅            | ✅                 | ❌                  |
| `git add -u` | ❌         | ✅              | ✅             | ✅            | ✅                 | ✅                  |

