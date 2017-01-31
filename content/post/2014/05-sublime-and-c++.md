---
date: 2014-09-09T18:29:00-07:00
description: "Last week started off with some C++ work. Leading me to learning makefiles, GCC, and how to use them with Sublime Text 3. I went with a simpler tool to force a better understanding on how the pieces fit together on myself."
title: "Sublime Build & Run C++"
draft: false
topics:
- how-to
type: post
---

Last week started off with some C++ work. Leading me to learning makefiles, GCC, and how to use them with Sublime Text 3. I went with a simpler tool to force a better understanding on how the pieces fit together on myself. Full IDEs cover the details up. Not as effective when you want to learn about those details.

ST3's build system is simple enough. Looking at the built in build configurations I put together what I wanted mine to do. It comes with a makefile build, but I wanted a build and run feature (Ctrl+Shift+B). 

If I were to write `"cmd":["App.exe"]` ST3 will run App.exe inside its own REPL console. This was a problem since it prevented me from interacting with my little learning programs. I'll skip the tedious part of the journey. The working result is this:

    "shell": true,
    "cmd": [
       "make", "exeName=${project_base_name:App}", "&&",
       "start", "${project_base_name:App}"
    ]

The `"shell":true` statement is the key here. Now ST3 will run the commands in the OS's shell (cmd or bash). This means I can separate commands with `&&` and launch programs outside of the REPL console with `start`. I had thought commands ran in the shell until I discovered this.

With the `"name":"Run"`, this will fire from a hotkey. Little things like this make for a nice workflow.

Here's the full [sublime-build file](https://cosmicbagel.com/static/Make.sublime-build)