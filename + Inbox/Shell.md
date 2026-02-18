# Intro to shell scripts in Terminal on Mac

A _shell script_ is a text file that contains one or more UNIX commands. You run a shell script to perform commands you might otherwise enter at the command line.

A shell script begins with a character combination that identifies it as a shell script—specifically the characters # and ! (together called a _shebang_) followed by a reference to the shell the script should be run with. For example, here’s the first line of a shell script that would be run with `sh`:

`#!/bin/sh`

You use the `chmod` tool to indicate that the text file is executable (that is, its contents can run as a program). See [Make a file executable in Terminal](https://support.apple.com/en-au/guide/terminal/make-a-file-executable-apdd100908f-06b3-4e63-8a87-32e71241bab4/2.14/mac/15.0).

For information about how to write shell scripts, see the [Shell Scripting Primer](https://developer.apple.com/library/mac/#documentation/OpenSource/Conceptual/ShellScripting) on the Apple Developer website.

## Zsh

- Starting with the _Catalina_ version of macOS, the default shell has been switched to **Zsh**. See [Apple Support article: Use zsh as the default shell on your Mac](https://support.apple.com/102360) for more information. 

- You can (and should) edit `~/.zshrc` to customise your shell. It is strongly recommended to keep all shell customisation and configuration (including exported environment variables such as `PATH`) in `~/.zshrc` or in files sourced from `~/.zshrc`. 

- Zsh supports several additional startup files with complex rules governing when each file is sourced. The additional startup files are `~/.zprofile`, `~/.zlogin`and `~/.zlogout`. **Do not create these files** unless you are absolutely certain you need them.

## Resources & Guides 

[POSIX `sh(1)` specification](https://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html)
[https://linuxjourney.com/lesson/the-shell](https://linuxjourney.com/lesson/the-shell)

## Tools

[https://brew.sh/](https://brew.sh/)
[https://ohmyz.sh/](https://ohmyz.sh/)
