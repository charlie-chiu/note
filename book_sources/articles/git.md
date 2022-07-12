
# compare git branches
```bash
git diff branch1..branch2
```
注意：兩點及三點的結果不同。

顯示的格式為 branch1 -> branch2 間的變化

`--- some.file` 代表 branch1 有some.file，branch2則否

```bash
git log master..branch
```
[so](https://stackoverflow.com/questions/13965391/how-do-i-see-the-commit-differences-between-branches-in-git)

# delete all local branch expect master, develop and release
```bash
git branch | grep -v -e "master" -e "develop" -e "release"  | xargs git branch -D
```

- `v` mean "invert match"

# reset --hard to origin match branch
```bash
git reset --hard @{upstream}
```

# .gitignore改變後重整檔案
```bash
git rm -r --cached .
git add .

git commit -m "fixed untracked files"
```

# git diff

```bash
git diff

git diff --cached
```

