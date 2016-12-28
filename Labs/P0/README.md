# Lab 0: Intro to the lab & Warmup

[TOC]

## Objetives

* Prepare the information structure in gitlab.com
* Familiarize yourself with the working environment
* Refresh your C knowledge and tools use

## Overview

LAB designed to get used to the tools used in forthcoming labs and refresh OS course tools.

## Steps

1. Accept the invitation to gitlab. Create and account there.
2. Fork the material repository in a private repository, creating a branch with your DNI.
3. Invite to such repository to vpuente@gmail.com
4. Wait for all
5. Update your repository with the new update
6. Rebase your code
7. Create a vagrant instance in the top level directory
8. Create a [Fast Short](## Fast Sort Program) program (see next section). it inside vagrant
9. Commit the changes into your branch and push them to gitlab
10. Write a guide with all the details in this directory and push them to gitlab again

## Fast Sort Program

You will write a simple sorting program. This program should be invoked as follows:

`shell%./fastsort [ -3] file`

The above line means the users typed in the name of the sorting program `./fastsort` and gave it one or two inputs. If just one input is given, the input file `file` should be sorted and the sorted output printed to the screen; it is assumed that the file is a text file (full of ASCII characters) and, when no other arguments are given, the sorting should be over the first word in each line.

If the optional argument is included ( `-3` in the example), the program should sort the text input file using the specified word as the key to sort upon (with `-3` , the program should find the 3rd word in each line and sort the lines based upon that).

### Examples

Let's say you have the following file:

<pre>this line is first
but this line is second
finally there is this line
</pre>

If you run your fastsort and give it this file as input, it should print:

<pre>but this line is second
finally there is this line
this line is first
</pre>

because `but` is alphabetically before `finally` is before `this` .

If, however, you pass in a flag to sort a different key, you'll get a different output. For example, if you call `fastsort -2` on this file, you should get:

<pre>this line is first
finally there is this line
but this line is second
</pre>

because `line` comes before `there` comes before `this` . Yes, we are assuming `-2` means the second word in each line (like most people would, except computer scientists who always want to start at 0).

### Hints

In your sorting program, you should just use `fopen()` to open the input file, `fgets()` to read each line of the file, and `fclose()` when you are done with the input file.

If you want to figure out how big in the input file is before reading it in, use the `stat()` or `fstat()` calls.

To compare strings, use the `strcmp()` library call.

To sort the data, use any sort that you'd like to use. An easy way to go is to use the library routine `qsort()` .

To chop lines into words, you could use `strtok()` . Be careful, though; it is destructive and will change the contents of the lines. Thus, if you use it, make sure to make a copy of the line to output.

The routine `atoi()` (or better yet, `strtol()` ) can be used to transform a string into an integer.

To exit, call `exit()` with a single argument. This argument to exit() is then available to the user to see if the program returned an error (i.e., return 1 by calling `exit(1)` ) or exited cleanly (i.e., returned 0 by calling `exit(0)` ). You can also just return from the `main()` function and pass the return code that way where appropriate.

The routine `malloc()` is useful for memory allocation. Make sure to exit cleanly if malloc fails!

If you don't know how to use these functions, use the man pages. For example, typing `man qsort` at the command line will give you a lot of information on how to use the library sorting routine.

## Assumptions and Errors

* **The return code upon success is zero.** When the program runs normally and no errors are encountered, you should return an error code of 0.

* **Only space characters (i.e., what you get when you hit spacebar) will be used to separate words in the input.** Thus, you don't have to worry about tabs or other whitespace. However, your program should correctly handle the case where there are two or more spaces between words, i.e., it should treat that as one big separator between the words.

* **Max line length will be 128.** If you get a line longer than this (detected by the lack of a newline character in the last position), please print `Line too long` to standard error and exit with return code 1.

* **You should check the arguments of fastsort carefully.** If more than two arguments are passed, or two are passed but the second does not fit the format of a dash followed by a number, you should EXACTLY print (to standard error): `Error: Bad command line parameters` and exit with return code 1.

* **Key does not exist on one line of input file:** If the specified key does not exist on a particular line of the input file, you should just use the last word of that line as the key. For example, if the user wants to sort on the 4th word ( `-4` ), and the sort encounters a line like this ( `sample line` ), the sort should use the word `line` to sort that line.

* **Empty line:** You should use an empty string to sort any empty lines (i.e., lines that are just a newline or spaces and a newline character).

* **File length:** May be pretty long! However, no need to implement a fancy two-pass sort or anything like that; the data set will fit into memory and you shouldn't have to do anything special to handle this. However, if malloc() does fail, please print `malloc failed` to standard error and exit with code 1.

* **Invalid files:** If the user specifies an input file that you cannot open (for whatever reason), the sort should EXACTLY print (to standard error): `Error: Cannot open file foo` with no extra spaces (if the file was named `foo` ) and then exit with return code 1.

**Important:** On any error code, you should print the error to the screen using `fprintf()` , and send the error message to `stderr` (standard error) and not `stdout` (standard output). This is accomplished in your C code as follows:

`fprintf(stderr, “whatever the error message is\n”);`

### General Advice
**Start small, and get things working incrementally.** For example, first get a program that simply reads in the input file, one line at a time, and prints out what it reads in. Then, slowly add features and test them as you go.

**Testing is critical.** One great programmer I once knew said you have to write 5-10 lines of test code for every line of code you produce; testing your code to make sure it works is crucial. Write tests to see if your code handles all the cases you think it should. Be as comprehensive as you can be. (Don't rely in C compiler but -Wall can be useful!)


**Use git.** commit your changes frequently, as you may introduce bugs and not be able to easily undo them. A simple way to do this is to use commits, by explicitly making copies of the file at various points during development. The old way is to use copies. For example, let's say you get a simple version of `fastsort.c` working (say, that just reads in the file); type `cp fastsort.c fastsort.v1.c` to make a copy into the file `fastsort.v1.c` .**DONT DO IT THAT WAY**. Instead **USE GIT**. Git is designed to avoid this hashle: you can keep a constant timeline of your code. So, make frequent commits into the repository. Push to the server when you leave the lab. Put all code for this lab inside the dir **Projects/P0/**  

**Keep your source code private.** Your gitlab repository only can be seen by the professor. Note that to copy is not allowed (and can be easily detected with automated tools such as [this](https://theory.stanford.edu/~aiken/moss/)).


## Reference


**Before beginning:** Read [OSTEP tutorial](http://pages.cs.wisc.edu/~remzi/OSTEP/lab-tutorial.pdf). It has some useful tips for programming in the C environment.

A nice guide for **git** can be found [here](https://www.atlassian.com/git/tutorials/what-is-version-control). The subset used here is quite sparse. In particular we need to do git clone/git pull/git push/git commit/git add and git rebase.

**Vagrant** information can be found [here](https://www.vagrantup.com/docs/getting-started/). Although it is quite useful, we will use here just as _simplication tool_. Shared folders allow to use the text editor you want in the host. Yes you can use Eclipse (although I recommend to take a look to others such as [Atom](http://atom.org/), [SublimeText](https://www.sublimetext.com/3), [Visual Code](https://code.visualstudio.com) or **VIM**😬). Try and pick your poison. Some of them has a nice git integration.

**Video Tutorial (Spanish)**

[![Intro (spanish)](http://img.youtube.com/vi/W15-Yx_zdsc/0.jpg)](https://www.youtube.com/watch?v=W15-Yx_zdsc)

# Evaluation
You dont need to do anything to handin the material.  The profesor will run a script at deadline date 00:00AM, grabbing all the material in ur repository. Any further change beyond this date will be ignored. This course, this material will be considered as a +10% extra to your final grade (yes, u can get a 11). The evaluation will be supported (experimentally) by automatic scripts.


