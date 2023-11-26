---
title: "Delete older git branches"
date: 2023-08-01
description: >-
  Delete git branches older than given number of days/weeks/months
tags:
  - bash
  - git
categories:
  - git
---

Every few months, I find myself finding the command to delete all my old branches. To the future me,

<!--more-->

```
for k in $(git branch | sed /\*/d); do
  if [ -z "$(git log -1 --since='1 week ago' -s $k)" ]; then
    git branch -D $k
  fi
done
```
