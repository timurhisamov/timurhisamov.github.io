---
layout: post
title: git-profile switch
subtitle: Each post also about .ssh/config settings
---

Then I try to start this blog, I need to switch git profiles between work and home.

Git-profile utility makes profile switch in local repository:
[git-profile](https://github.com/dotzero/git-profile)

Install like pascal programmer's:
```bash
brew install dotzero/tap/git-profile
```

After we need to provide profiles `work` and `home` with emails and ssh.pub keys

Then, I tried to push commits to origin and it was failed. Push called global profile. Next step is change ssh config. This article helped: [link](https://medium.com/@therajanmaurya/git-push-pull-with-two-different-account-and-two-different-user-on-same-machine-a85f9ee7ec61)

Commands for zoomers and lazy people like me:
```bash
vim ~/.ssh/config
-----------------
#work
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_work
#home
Host github-home
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_home
```
```bash
git clone git@github.com/<repo dir>
cd <repo dir>
vim .git/config
#change github.com to github-home address in origin
git-profile use home
#check configs by
git config --list
git add .
git commit -m "push from home"
git push origin master
```
