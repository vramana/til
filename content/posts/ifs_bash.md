---
date: 2023-07-13
title: Concatenate comma separated strings in bash
description: >-
  Arrays & Internal field seperator in bash
tags:
  - bash
  - string
  - arrays
  - programming
  - chatgpt
categories:
  - bash
---

I learnt how to concatenate an array of strings in bash using ChatGPT.

<!--more-->

To declare an array of strings in bash, you can write it following way:

```bash
ARRAY_STRINGS=(
    "APPLE"
    "BANANA"
    "FIG"
    "ORANGE"
    "PINEAPPLE"
    "STRAWBERRY"
)
```

If you echo `ARRAY_STRINGS`, the output will be only `APPLE`. To print
the entire array, you can write the following code:

```bash
echo "${ARRAY_STRINGS[*]}"

# It will print
#
# APPLE BANANA FIG ORANGE PINEAPPLE STRAWBERRY
```

`[*]` notation expands the entire array and then substitutes all the words in echo.
That's how we are able to print the whole array. This can also be used to iteration.

```bash
for element in "${ARRAY_STRINGS[*]}"; do
    echo "$element"
done
```

What if we want to concatenate strings with commas or some other character.
You can use `IFS` (internal field separator). It is an environment variable in bash
that controls string splits into words or how strings concatenate in command
substitution. In this case  when array is substituted in using `[*]`, elements are joined
by the first character of `IFS`.


```bash
original_ifs=$IFS
IFS=","

echo "${ARRAY_STRINGS[*]}"

IFS=$original_ifs

# It will print
#
# APPLE,BANANA,FIG,ORANGE,PINEAPPLE,STRAWBERRY
```


**Context**: I encountered this problem when writing google cloud functions deploy command. I have to pass
a more than 5 secrets to this and the command was super long. I refactored it using an array of
strings and environment variables in bash.


