---
title: CSC209 Week1
date: 2023-09-12 14:19:06
tags: [CSC209, cs, uoft, c, notes]
category: [Notes, Year2, CSC209]
---

# Unix basics

## Directory structure

- Top level folder: root directory `/`
- Each non-directory is a leaf
- directores contain directores and files

## Commands

`cd`, `ls`, `pwd`

every command is a program, the things you type after the program are *arguments* to the program

```bash
cd /
```

`cd` is the program, `/` is the argument.

```bash
cd, mkdir, ls, cp, mv, rm

cat, grep, head, tail
```

## Path

Path is separated by `/`, useful shorthands

- `..`: up 1 directory
- `~`: home directory

### Long listing

`ls -l`

permission, user, user group, creation date

### Execute program

- three files associated to program we run:
  - `stdin`, `stdout`, `stderr`

- terminals: type into `stdin`, view `stdout`, `stderr`
- shell: run program with arguments, view `stdout`, `stderr`

## Useful features of shell

### Piping
`|` operator: make stdout of one program to be the other program's stdin

```bash
ls -l | head -n 1
```

the output of `ls -l` becomes input of `head -n 1`

* -n 1 is how many lines `head -n 1` outputs (default 10)
* you can add many lines

### Redirection

`>`: change stdout to be some other file
`<`: change the input to be from some other file (as if the file is typing the keyboard)

### Globing

pass regex-like patterns as directory

- `*` any
- `?` any one character
- `[]` possible characters
  - `[0-5]`

# C basics

## compile
- `gcc` gnu compiler collection
```Bash
  gcc -o hello hello.c
```
- Some more arguments:
  - `-Wall` all warnings
  - `-std=gnu99` specify standard
  - *`-g` use gdb*

## Main entry
```C
int main(int argc, char* argv[]);
```

- `argc`: argument count (including name of the executable)
- `argv`: array of all the arguments