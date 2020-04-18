---
layout: post
title: git push --force
subtitle: do it at own risk
---

typical picture in pull request, then u test you infrastructure:
![typicall pic](/img/force-push.png)

i would squash this commits in ONE commit:
```bash
git checkout my_branch
git reset --soft HEAD~5
git commit -m "all fixes in this commit"
git push --force origin my_branch
```
