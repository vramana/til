---
title: "Concurrent processes in bash"
date: 2023-07-15
description: >-
  Arrays & Internal field seperator in bash
tags:
  - parallel
  - bash
  - concurrency
  - programming
  - process
categories:
  - bash
---

I learned how to spawn background process in bash and wait for them to finish.

<!--more-->

Take the following script, we have to 2 process that slow and running sequentially.

```bash
process1_fn() {
  echo "Hello from process 1";
  sleep 5;
  echo "End of process 1"
}

process2_fn() {
  echo "Hello from process 1";
  sleep 5;
  echo "End of process 1"
}

process1_fn
process2_fn
```

How do we make them run concurrently? We can kick of each process independently using `&` operator.
We can use `wait` command to wait for all the process to end.

```bash
process1_fn() {
  echo "Hello from process 1";
  sleep 5;
  echo "End of process 1"
}

process2_fn() {
  echo "Hello from process 2";
  sleep 5;
  echo "End of process 2"
}

process1_fn &
process2_fn &

wait
```

**Context**: I ran into this problem while deploying multiple cloud functions in Google Cloud Build.
Deploying each cloud function takes about 3 mins. So, I used this technique to reduce my deployment
time.
