---
title: "HTB Apocalypse 2023 - Shattered Tablet"
date: 2023-04-01T10:33:50+02:00
author: mara
tags:
- "HTB Apocalypse 2023"
- "Reversing"
- "Python"
- "Python 3"
- "IDA Freeware"
- "IDA"
- "IDA Decompiler"
---

# Shattered Tablet's writeup

We analysing the file named `tablet` to identify its characteristics :

```sh
$ file tablet
tablet: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=efa8165e123acf37caf4e4b73aba0b826efae1f1, for GNU/Linux 3.2.0, not stripped
```

File utility seems returns it's a non **stripped** **x64_64** Linux binary executable. In another words, some debugging symbols can be present. It's a good new our deep dive analysis.

Let's open the `tablet` file in `IDA Freeware 7.x` to use the online decompiler if needed.

The first point will be to find the real entrypoint, here the function `__libc_start_main_ptr` can help us.

```assembly
.text:0000000000001070 _start          proc near               ; DATA XREF: LOAD:0000000000000018↑o
.text:0000000000001070                 xor     ebp, ebp
.text:0000000000001072                 mov     r9, rdx         ; rtld_fini
.text:0000000000001075                 pop     rsi             ; argc
.text:0000000000001076                 mov     rdx, rsp        ; ubp_av
.text:0000000000001079                 and     rsp, 0FFFFFFFFFFFFFFF0h
.text:000000000000107D                 push    rax
.text:000000000000107E                 push    rsp             ; stack_end
.text:000000000000107F                 lea     r8, __libc_csu_fini ; fini
.text:0000000000001086                 lea     rcx, __libc_csu_init ; init
.text:000000000000108D                 lea     rdi, main       ; main             <=== interesting
.text:0000000000001094                 call    cs:__libc_start_main_ptr
.text:000000000000109A                 hlt
.text:000000000000109A _start          endp
```

Following up the `main` function :

To be continued...
