# Project: xv6 Intro
[TOC]

We'll be doing kernel hacking projects in **xv6.** Xv6 is a port of a classic version of unix to a modern processor, Intel's x86\. It is a clean and beautiful little kernel, and thus a perfect object for our study and usage.

This first project is just a warmup, and thus relatively light on work. The goal of the project is simple: to add a system call to xv6\. Your system call, **getprocs()** , simply returns how many processes exist in the system at the time of the call.

## Details

Your new syscall should look like this: **int getprocs(void)**. Your system call returns the number of processes that exist in the system at the time of the call.

## Tips

Find some other system call, like **getpid()** or any other simple call. Basically, copy it in all the ways you think are needed. Then modify it to do what you need.

Most of the time will be spent on understanding the code. There shouldn't be a whole lot of code added.

To write user programs in **xv6** (and try your implementation) try to understand how the code in **xv6/user/** is made accessible to the systema at boot.

Using gdb (the debugger) may be helpful in understanding code, doing code traces, and is helpful for later projects too. Get familiar with this fine tool!

A perfect way to start with it is "booting" xv6, adding a "Hello World" program. Try to understand all the steps in place. You might need to refresh your 
knowledge about Makefiles.

## The Code

This kernel was developed by [MIT OS Enegeneering](https://pdos.csail.mit.edu/6.828/2016/). Nevertheless, the version used here has been "reorganized" by OSTEP author. We will use that version (which is avaliable in **../xv6/xv6-wisc/**).

You may also find the following readings about xv6 useful, written by the same team that ported xv6 to x86: [xv6 book.](https://pdos.csail.mit.edu/6.828/2014/xv6/book-rev8.pdf) However, remeber that the kernel version we use is a little different than the book.

## Environement

Use at least version 1.21 of vpuente/AOSUC1516 vagrant box. This box includes all the tools required to perform the project (gcc, qemu, shared dirs with the guest, etc...). Alternativelly you can create your own "tailored" box. Any linux will be fine! (you can use also port or homebrew on OSX but requires some tinkering witht he compilers).

## Reference

[![Intro (spanish)](http://img.youtube.com/vi/7B-P9m29wFk/0.jpg)](https://www.youtube.com/watch?v=7B-P9m29wFk)


**Particularly useful for this project: Chapter 6 (Direct Execution).**



