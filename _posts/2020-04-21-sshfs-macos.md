---
layout: post
title: sshfs filesystem on macOS
---

This short guide is about connecting my Raspberry PI 3 to macbook with macOS Catalina.

Install sshfs on macOS. I use version of `osxfuse = 3.10.4`:
```bash
brew cask install osxfuse
brew install sshfs
mkdir ~/sshfs
ssh-copy-id pi@raspberrypi
```

When on Raspberry PI lets mount vfat fs with special rights:
```bash
sudo mount -t vfat /dev/sda1 /mnt -o rw,uid=1000,gid=1000
```

Next, try to connect sshfs to my mac. SSH to Raspberry PI:
```bash
sshfs pi@raspberrypi:/mnt/ ~/sshfs
```

Open Finder and check your success.
![sshfs pic](/img/sshfs.png)
