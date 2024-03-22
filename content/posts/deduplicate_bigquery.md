---
title: "Deduplicate rows in BigQuery table"
date: 2023-09-24T16:37:11+05:30
draft: true
tags:
  - bigquery
  - sql
---

There are few solutions on the Stack Overflow, Medium blogs and other places but
none of them solved my particular use case.

<!-- more -->

Problem:

Data is continuously written to a BigQuery table. Sometimes a row may be written
twice. So we need to deduplicate the rows in this table where the rows are exactly
identical.

BigQuery doesn't expose an internal row ID that we can use to segregate these rows.
We can't replace the table in-place or create a new table which is the
most common suggestion in the solutions.
