---
layout: post
title: Automating Notes
date: 2025-4-1 15:00:00
description:
tags: workflow
categories: 
thumbnail: 
---

Previously, I've written on Medium about how I use Obsidian for notetaking and how it's been a very large part of how I get through schoolwork and learning things in general. Recently, I've finally done something I should've done a long time ago, which is to move away from Google Drive and use Git for version control.

Below is my current backup script, automated with crontabs to run every night at 11 pm. The right thing to do is to put this script up as a Github Gist, but I felt that an article on my site seems more organized.

To do this for yourself is pretty easy. Store your notes somewhere locally or something that is accessible by your file system. Start a git repository in that directory and set as the remote an empty repository on Github. You'll need to authenticate with the command-line Github authenticator for this to work.

```bash
#!/bin/bash

current_date=$(date '+%Y-%m-%d')
dir=my/notes/directory/on/Google/Drive

# Attempting to zip files for local backup

num_files=$(ls -1 "$dir" | wc -l)

echo "Attempting to zip $dir, which contains $num_file files for local backup..."

{

zip -rq ~/Documents/Backups/Notes/"$current_date".zip "$dir"/* && echo "Success. Backup created $current_date" 

} || {

echo "Backup failed."

}

# Push Changes to Github
echo "Attempting to commit and push changes to GitHub..."

cd "$dir" || { echo "Failed to cd into $dir"; exit 1; }

# Check for changes
if [ -n "$(git status --porcelain)" ]; then
    git add .
    git commit -m "Daily backup auto-commit: $current_date"
    git push origin main || echo "Git push failed."
else
    echo "No changes to commit."
fi

# Deleting files older than 3 days
echo "Attempting to delete files older than 3 days"
{

find ~/Documents/Backups/Notes -mindepth 1 -mtime +3 -delete

} || {

echo "Failed to delete files older than 3 days"

}
```