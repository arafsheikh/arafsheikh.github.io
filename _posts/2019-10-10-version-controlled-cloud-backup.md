---
layout:	post
title: Version Controlled Cloud Backup
date: 2019-10-10 03:11:00
---

I've longed for a (hobby) home server for quite a while. So a couple of weeks ago I pulled the trigger and bought myself a Raspberry Pi. As soon as I received it I hooked it in and began my odessey into the world of server administration and self-hosted services. I swiftly set-up a SSH server, SMTP mail server, reverse proxy, database, feed reader, and a bunch of home automation scripts. With all these services came a ton of configuration files that need to backup to a remote location lest I do something stupid and lose them. After all I have a habit of tinkering around too much 🤷‍♂️.

## The brains of the solution

I wanted a free and hackish solution, one that allowed me to use the tools I'm already familiar with. Most of the files I wanted to backup were text so I thought – why not use git! Using git would have the added advantage of version control, so I can go back to an older revision of my files – something very useful when I'm constantly fiddling with the config. 

I scouted around the Interwebs for a tool to copy my files and directories into a local git repository. I stumbled upon `rsync` – a good 'ol (circa [1996](https://en.wikipedia.org/wiki/Rsync#History)) Unix utility to maintain a two directories on different systems in-sync. But it can also be used to  maintain in-sync replicas of files and directories within a machine. Perfect!

## What about binary files?

I also wanted to backup my databse dump. Since the database can get large quickly I decided to gunzip the dump file. Now I had a binary file that could become reasonably large over time and will be diff-ed and commited by git everytime I ran the backup scipt. 

### Git LFS to the rescue!

Git's Large File System extension allows stroing the binary files in a seperate location and only commiting the latest pointer to the file in the git repository. This way it's much quicker to clone the repository back as only the last revision of the binary file is downloaded. Plus, the commits look cleaner ✨.

## Putting it all together

Now that I had all the pieces figured out, I wrote a script that initializes the local git repository, runs `rsync` on a set of files and directories and pushes them onto Github. Then I set a cron job to run this script every hour and voila!

```bash
#!/bin/bash

(( EUID != 0 )) && exec sudo -- "$0" "$@" # become root

mkdir -p /home/pi/backup
git init --quiet /home/pi/backup
git -C /home/pi/backup lfs install > /dev/null
git -C /home/pi/backup lfs track "*.gz" > /dev/null
git -C /home/pi/backup add .gitattributes > /dev/null
git -C /home/pi/backup remote add origin git@github.com:arafsheikh/rpi-backup.git 2>/dev/null
git -C /home/pi/backup config --local user.email "pi@raspberrypi"
git -C /home/pi/backup config --local user.name "RPi"

rsync_out=$(rsync -aR --delete -v \
	/home/pi/scripts \
	/home/pi/services \
	/home/pi/server/nginx/conf \
	/home/pi/server/nginx/ssl \
	/home/pi/.config \
	/home/pi/.ssh/authorized_keys \
	/home/pi/.bashrc \
	/var/spool/cron/crontabs/pi \
	/etc/ssmtp/ssmtp.conf \
	/etc/sudoers.d/custom \
	/var/lib/postgresql/dump.gz \
	/home/pi/backup)

if [ $? -ne 0 ]; then
	>&2 echo 'Error occured running rsync'
fi

git -C /home/pi/backup add .
git -C /home/pi/backup diff-index --quiet HEAD || git -C /home/pi/backup commit --quiet -m "update backup" -m "$rsync_out"
git -C /home/pi/backup push --quiet origin master > /dev/null
```

I've been using this for a couple of days now and I'm surprised by how well it works. Gives you peace of mind when all the inestimable parameters in your configuration files that you've meticulously tweaked over several hours are safely backed-up in the clouds.

![](/images/rpi-cloud-backup.png)
