## nnn

Noice is Not Noice, a noicer fork...

<p align="center">
<a href="https://github.com/jarun/nnn/releases/latest"><img src="https://img.shields.io/github/release/jarun/nnn.svg?maxAge=600" alt="Latest release" /></a>
<a href="https://aur.archlinux.org/packages/nnn"><img src="https://img.shields.io/aur/version/nnn.svg?maxAge=600" alt="AUR" /></a>
<a href="http://braumeister.org/formula/nnn"><img src="https://img.shields.io/homebrew/v/nnn.svg?maxAge=600" alt="Homebrew" /></a>
<a href="https://packages.debian.org/search?keywords=nnn&searchon=names"><img src="https://img.shields.io/badge/debian-10+-blue.svg?maxAge=2592000" alt="Debian Buster+" /></a>
<a href="https://launchpad.net/~twodopeshaggy/+archive/ubuntu/jarun/"><img src="https://img.shields.io/badge/ubuntu-PPA-blue.svg?maxAge=2592000" alt="Ubuntu PPA" /></a>
<a href="https://github.com/jarun/nnn/blob/master/LICENSE"><img src="https://img.shields.io/badge/license-BSD%202--Clause-yellow.svg?maxAge=2592000" alt="License" /></a>
<a href="https://travis-ci.org/jarun/nnn"><img src="https://travis-ci.org/jarun/nnn.svg?branch=master" alt="Build Status" /></a>
</p>

[![nnn screencast](https://s16.postimg.org/h8ha5z69x/nnn_demo.png)](https://vimeo.com/215489406 "Click for some action!")

<p align="center"><a href="https://vimeo.com/215489406">Click for some action!</a></p>

### Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Performance](#performance)
- [Installation](#installation)
- [Usage](#usage)
  - [Cmdline options](#cmdline-options)
  - [Keyboard shortcuts](#keyboard-shortcuts)
  - [Filters](#filters)
  - [Navigate-as-you-type mode](#navigate-as-you-type-mode)
  - [File type abbreviations](#file-type-abbreviations)
  - [File handling](#file-handling)
  - [Help](#help)
- [Quickstart](#quickstart)
- [How to](#how-to)
  - [add bookmarks](#add-bookmarks)
  - [use cd .....](#use-cd-)
  - [cd on quit](#cd-on-quit)
  - [copy file path to clipboard](#copy-file-path-to-clipboard)
  - [file copy, move, delete](#file-copy-move-delete)
  - [boost chdir prompt](#boost-chdir-prompt)
  - [set idle timeout](#set-idle-timeout)
- [Why fork?](#why-fork)
- [Mentions](#mentions)
- [Developers](#developers)

### Introduction

`nnn` is a fork of [noice](http://git.2f30.org/noice/), a blazing-fast lightweight terminal file browser with easy keyboard shortcuts for navigation, opening files and running tasks. noice is developed considering terminal based systems. There is no config file and mime associations are hard-coded. However, the incredible user-friendliness and speed make it a perfect candidate for modern distros.

`nnn` works with the desktop opener, adds new navigation options, [navigate-as-you-type](#navigate-as-you-type-mode) mode, enhanced DE integration, bookmarks, a disk usage analyzer mode, comprehensive file details and much more. Add to that a huge [performance](#performance) boost. For a detailed comparison, visit [nnn vs. noice](https://github.com/jarun/nnn/wiki/nnn-vs.-noice).

If you want to edit a file in vim with some soothing music in the background while referring to a spec in your GUI PDF viewer, `nnn` got it! [Quickstart](#quickstart) and see how `nnn` simplifies those long desktop sessions...

Have fun with it! PRs are welcome. Check out [#1](https://github.com/jarun/nnn/issues/1).

<p align="center">
<a href="https://saythanks.io/to/jarun"><img src="https://img.shields.io/badge/say-thanks!-ff69b4.svg" /></a>
<a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=RMLTQ76JSXJ4Q"><img src="https://img.shields.io/badge/PayPal-donate-FC746D.svg" alt="Donate via PayPal!" /></a>
</p>

### Features

- Navigation
  - Familiar shortcuts
  - *Navigate-as-you-type* mode
  - Bookmarks
  - Jump HOME or to the last visited directory (as usual!)
  - Jump to initial dir, chdir prompt, cd ..... (with . as PWD)
  - Roll-over at edges, page through entries
- Disk usage analyzer mode
- Search
  - Filter directory contents with *search-as-you-type*
  - Desktop search (default gnome-search-tool, customizable) integration
- Mimes
  - Desktop opener integration
  - Optionally open text files in EDITOR (fallback vi)
  - Customizable bash script [nlay](https://github.com/jarun/nnn/wiki/all-about-nlay) to handle actions
- Information
  - Basic and detail view
  - Detailed file information
  - Media information (needs mediainfo)
- Ordering
  - Numeric order (1, 2, ... 10, 11, ...) for numeric names
  - Sort by modification time, size
- Convenience
  - Spawn a shell in the current directory
  - Invoke file path copier (*easy* shell integration)
  - Change directory at exit (*easy* shell integration)
  - Open any file in EDITOR (fallback vi) or PAGER (fallback less)
  - Open current directory in a custom GUI file browser
  - Terminal screensaver (default vlock, customizable) integration
- Unicode support
- Highly optimized code, minimal resource usage

### Performance

`nnn` vs. ncdu memory usage while listing 438767 files in disk usage analyzer mode:

```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
22515 vaio      20   0   60348  48712   2240 S   0.0  0.6   0:01.11 ncdu /
22574 vaio      20   0   17588   4320   2584 S   0.0  0.1   0:00.44 nnn /
```

`nnn` vs. mc vs. ranger memory usage while viewing a directory with 11244 files, sorted by size:

```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
28450 vaio      20   0   93848  51548   7724 S   0.0  0.6   0:00.64 /usr/bin/python -O /usr/bin/ranger
27265 vaio      20   0   67188  13620   6908 S   0.0  0.2   0:00.16 mc
28360 vaio      20   0   20520   6932   2512 S   0.0  0.1   0:00.20 nnn
```

### Installation

`nnn` needs libreadline, libncursesw (on Linux or ncurses on OS X) and standard libc.

- Packages are available on
  - [AUR](https://aur.archlinux.org/packages/nnn/)
  - [Homebrew](http://braumeister.org/formula/nnn)
  - [Debian](https://packages.debian.org/search?keywords=nnn)
  - [Ubuntu PPA](https://launchpad.net/~twodopeshaggy/+archive/ubuntu/jarun/)
- Packages for **Fedora 24** and **CentOS 7** are available with the [latest release](https://github.com/jarun/nnn/releases/latest)
- To cook yourself, download the [latest stable release](https://github.com/jarun/nnn/releases/latest) or clone this repository (*risky*). Then install the dependencies and compile (e.g. on Ubuntu 16.04):

      $ sudo apt-get install libncursesw5-dev libreadline6-dev
      $ make
      $ sudo make install

### Usage

#### Cmdline options

    usage: nnn [-l] [-i] [-p custom_nlay] [-S] [-v] [-h] [PATH]

    The missing terminal file browser for X.

    positional arguments:
      PATH           directory to open [default: current dir]

    optional arguments:
      -l             start in light mode (fewer details)
      -i             start in navigate-as-you-type mode
      -p             path to custom nlay
      -S             start in disk usage analyzer mode
      -v             show program version and exit
      -h             show this help and exit

`>` indicates the currently selected entry in `nnn`.

#### Keyboard shortcuts

```
                Key | Function
                   -+-
          Up, k, ^P | Previous entry
        Down, j, ^N | Next entry
           PgUp, ^U | Scroll half page up
           PgDn, ^D | Scroll half page down
     Home, g, ^, ^A | Jump to first entry
      End, G, $, ^E | Jump to last entry
Right, Enter, l, ^M | Open file or enter dir
  Left, Bksp, h, ^H | Go to parent dir
             Insert | Toggle navigate-as-you-type mode
                  ~ | Jump to HOME dir
                  & | Jump to initial dir
                  - | Jump to last visited dir
                  / | Filter dir contents
                 ^/ | Search dir in desktop search tool
                  . | Toggle hide .dot files
                  b | Show bookmark key prompt
                  c | Show change dir prompt
                  d | Toggle detail view
                  D | Toggle current file details screen
                  m | Show concise mediainfo
                  M | Show full mediainfo
                  s | Toggle sort by file size
                  S | Toggle disk usage analyzer mode
                  t | Toggle sort by modified time
                  ! | Spawn SHELL in PWD (fallback sh)
                  e | Edit entry in EDITOR (fallback vi)
                  o | Open dir in NNN_DE_FILE_MANAGER
                  p | Open entry in PAGER (fallback less)
                 ^K | Invoke file path copier
             ^L, F2 | Force a redraw, exit filter prompt
                  ? | Toggle help and settings screen
                  Q | Quit and change directory
              q, ^Q | Quit
```

#### Filters

Filters support regexes to instantly (search-as-you-type) list the matching entries in the current directory.

There are 3 ways to reset a filter: <kbd>^L</kbd> (or <kbd>F2</kbd>), a search with no matches or an extra backspace at the filter prompt (like vi).

Common examples: If you want to list all matches starting with the filter expression, start the expression with a `^` (caret) symbol. Type `\.mkv` to list all MKV files.

If `nnn` is invoked as root the default filter will also match hidden files.

#### Navigate-as-you-type mode

In this mode directories are opened in filter mode, allowing continuous navigation. Works best with the **arrow keys**.

#### File type abbreviations

The following abbreviations are used in the detail view:

| Symbol | File Type |
| --- | --- |
| `/` | Directory |
| `*` | Executable |
| <code>&#124;</code> | Fifo |
| `=` | Socket |
| `@` | Symbolic Link |
| `b` | Block Device |
| `c` | Character Device |

#### File handling

- `nnn` uses `xdg-open` on Linux and `open(1)` on OS X as the desktop opener.
- To edit all text files in EDITOR (preferably CLI, fallback vi):

        export NNN_USE_EDITOR=1
- To enable the desktop file manager key, set `NNN_DE_FILE_MANAGER`. E.g.:

        export NNN_DE_FILE_MANAGER=thunar
        export NNN_DE_FILE_MANAGER=nautilus
- [mediainfo](https://mediaarea.net/en/MediaInfo) is required to view media information

#### Help

    $ man nnn
To lookup keyboard shortcuts at runtime, press <kbd>?</kbd>.

### Quickstart

Add the following to your shell's rc file for the best experience:

1. Use a shorter and sweeter alias:

        alias n=nnn
2. Optionally open all text files in EDITOR (fallback vi):

        export NNN_USE_EDITOR=1
3. Set a desktop file manager to open directories with (if you ever need to). E.g.:

        export NNN_DE_FILE_MANAGER=thunar

Run `n`.

### How to

#### add bookmarks

Set environment variable `NNN_BMS` as a string of `key:location` pairs (max 10) separated by semicolons (`;`):

    export NNN_BMS='doc:~/Documents;u:/home/user/Cam Uploads;D:~/Downloads/'

#### use cd .....

To jump to the n<sup>th</sup> level parent, with PWD at level 0, use `n + 1` dots. For example, to jump to the 6<th> parent of the current directory, use 7 dots. If the number of dots would take you *beyond* `/` (which isn't possible), you'll be placed at `/`.

#### cd on quit

Pick the appropriate file for your shell from [misc/quitcd](https://github.com/jarun/nnn/tree/master/misc/quitcd) and add the contents to your shell's rc file. You'll need to spawn a new shell for the change to take effect. You should start `nnn` as `n` (or modify the function name to something else).

As you might notice, `nnn` uses the environment variable `NNN_TMPFILE` to write the last visited directory path. You can change it.

#### copy file path to clipboard

`nnn` can pipe the absolute path of the current file to a copier script. For example, you can use `xsel` on Linux or `pbcopy` on OS X.

Sample Linux copier script:

    #!/bin/sh

    echo -n $1 | xsel --clipboard --input

export `NNN_COPIER`:

    export NNN_COPIER="/path/to/copier.sh"

Start `nnn` and use <kbd>^K</kbd> to copy the absolute path (from `/`) of the file under the cursor to clipboard.

#### file copy, move, delete

`nnn` doesn't support file copy, move, delete inherently. However, it simplifies the workflow:

1. copy the absolute path to a file by invoking the file path copier (<kbd>^K</kbd>)
2. spawn a shell in the current directory (<kbd>!</kbd>)
3. while typing the desired command, copy the file path (usually <kbd>^-Shift-V</kbd>)

#### boost chdir prompt

`nnn` uses libreadline for the chdir prompt input. So all the fantastic features of readline (e.g. case insensitive tab completion, history, reverse-i-search) is available to you based on your readline [configuration](https://cnswww.cns.cwru.edu/php/chet/readline/readline.html#SEC9).

#### set idle timeout

The terminal screensaver is disabled by default. To set the wait time in seconds, use environment variable `NNN_IDLE_TIMEOUT`.

### Why fork?

I chose to fork because:
- one can argue my approach deviates from the goal of the original project -  keep the utility `suckless`. In my opinion evolution is the taste of time.
- I would like to have a bit of control on what features are added in the name of desktop integration. A feature-bloat is the last thing in my mind. Check out [nnn design considerations](https://github.com/jarun/nnn/wiki/nnn-design-considerations) for more details.

### Mentions

- [It's FOSS](https://itsfoss.com/nnn-file-browser-linux/)
- [FOSSMint](https://www.fossmint.com/nnn-linux-terminal-file-browser/)

### Developers

1. Copyright © 2014-2016 Lazaros Koromilas
2. Copyright © 2014-2016 Dimitris Papastamos
3. Copyright © 2016-2017 [Arun Prakash Jana](https://github.com/jarun)
