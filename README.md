# Introduction to handy

> by David Capello

## What's handy?

`handy` (or `handy-mode`) is a set of keyboard shortcuts that you
could use in (almost) any text editor. The idea is to offer a
progressive way to convert your current keyboard shortcuts to a more
easy to use set of shortcuts.

It's focused on Emacs, but you could (and we should try to provide)
ways to configure other text editors and even the
[Bash/readline](https://github.com/superhandy/inputrc) interpreter
or [zsh](https://github.com/superhandy/zshrc).

`handy` offers:

1. Simple cursor movements using the `Alt` modifier
2. A progressive path of change to incorporate new keyshortcuts step by step
3. And as a final stage, you will be able to use a modal mode (`vim`-like mode)
   where the same shortcuts are accesible without pressing `Alt` modifier all the time

## Motivation

Ten years ago (2009~2010) I started experiencing the [Emacs
pinky](https://en.wikipedia.org/wiki/Emacs#Emacs_pinky) problem.
Luckily, I've found a great project by Xah Lee:
[ErgoEmacs](http://ergoemacs.org/emacs/ergonomic_emacs_keybinding.html).
This was the beginning of a journey to re-learn all Emacs keyboard
shortcuts, and learning several good UX improvements like grouping
several Emacs commands in one keystroke or repetitive keystrokes.

After modifying ErgoEmacs for [my own
purposes](https://github.com/dacap/ergoprog), I decided to create a
[text editor](https://github.com/dacap/handy) with these shortcuts,
but it was a failed attempt (as it requires too much work/free-time to
finish it). So then the project changed to a more realistic approach:
create a progressive set of shortcuts to switch to `handy` from any
text editor (Emacs in the first place).

I'll try to include in this document the imagery that is on my own
head when I use `handy`, that will be helpful for new users to adopt
the new shortcuts.

## Keyboard Layout

This is the progressive set of levels that you will learn:

* [Level 1 JLIK](level-0-jlik) (*Jay's [Lick](https://en.wikipedia.org/wiki/Lick_(music))*-level): Move through characters and lines with `Alt+J`/`Alt+L`/`Alt+I`/`Alt+K`
* [Level 2 NM](level-1-nm) ([*Nanometre*](https://en.wikipedia.org/wiki/Nanometre)-level): Execute commands and cancel execution with `Alt+N`/`Alt+M`
* [Level 3 UO](level2-uo) ([*Unobtainium*](https://en.wikipedia.org/wiki/Unobtainium)-level): Move through words/paragraphs/functions with `Alt+U`/`Alt+O`
* [Level 4 ZB](level4-zb) ([*Zettabyte*](https://en.wikipedia.org/wiki/Zettabyte)-level): Undo/Cut/Copy/Paste and Buffers with `Alt+Z`/`Alt+X`/`Alt+C`/`Alt+V`/`Alt+B`
* [Level 5 YH](level-4-yh) ([*Yeah*](https://www.youtube.com/watch?v=GxBSyx85Kp8)-level): Incremental Search and End/Beginning-of-Line/Buffer Movement with `Alt+Y`/ `Alt+H`
* [Level 6 WERD](level-5-werd) ([*WERD*](https://youtu.be/Di9R9oA5Qzk?t=162)-level): Erase stuff with `Alt+W`/`Alt+E`/`Alt+R`/`Alt+D`/`Alt+D`/`Alt+F`/`Alt+G`
* [Level 7 Modal](level-6-modal) (*Modal*-level): Switch modes with `Alt+Enter`

### Level 1 JLIK

In the first level of `handy`, we have: `Alt+J`, `Alt+L`, `Alt+I`, `Alt+K`:

          .-----.
          |  I  |
    .-----'-----'-----.
    |  J  |  K  |  L  |
    '-----------------'

This set of keys simulate the arrow keys of any keyboard but they are
located in the home row mainly (JKL) so you don't have to move your
hand to move the cursor:

* `Alt+J`: Moves the cursor one character backward (e.g. Left Arrow, `backward-char` on Emacs)
* `Alt+L`: Moves the cursor one character forward (e.g. Right Arrow, `forward-char` on Emacs)
* `Alt+I`: Moves the cursor to the previous line (e.g. Up Arrow, `previous-line` on Emacs)
* `Alt+K`: Moves the cursor to the next line (e.g. Down Arrow, `next-line` on Emacs)

With the `Shift` modifier, steps get a little wider:

* `Alt+Shift+J`: Moves the cursor one balanced expression backward (e.g. `backward-sexp` on Emacs)
* `Alt+Shift+L`: Moves the cursor one balanced expression forward (e.g. `forward-sexp` on Emacs)
* `Alt+Shift+I`: Moves the cursor one page up (e.g. Page Up, `cua-scroll-down` on Emacs)
* `Alt+Shift+K`: Moves the cursor one page down (e.g. Page Down, `cua-scroll-up` on Emacs)

### Level 2 NM

                .-----.
                |     |
          .-----'     '-----.
          |                 |
    .-----'-----------------'
    |  N     M  |
    '-----------'

The second `handy` level enables the prefix key to open an huge range
of commands, and to cancel actions/commands:

* `Alt+M, ...`: Prefix key for other keys shortcuts (like `Ctrl+K` on VSCode, or `Ctrl+C` on Emacs)
* `Alt+Shift+M`: Execute command by name (e.g. `Ctrl+P` on VSCode, or `execute-extended-command` on Emacs)
* `Alt+N`: Cancels the execution of a command or prefix keys (e.g. `Esc` key, or `Ctrl+G` on Emacs)
* `Alt+Shift+N`: Creates a new untitled file (e.g. like `Ctrl+N` command in regular desktop apps)

List of `Alt+M, ...` commands:

* `Alt+M, F`: Open a file (e.g. `Ctrl+O` on VSCode, or `find-file` on Emacs)
* `Alt+M, D`: Open a folder/directory (e.g. `ido-dired` on Emacs)
* `Alt+M, S`: Save the file (e.g. `Ctrl+S` on regular desktop apps, or `save-buffer` on Emacs)
* `Alt+M, G`: Jump to a specific line number (e.g. `Ctrl+G` on VSCode, or `goto-line` on Emacs)

Commands about macros:

* `Alt+M, M`: Start (and then Stop) recording a macro (`handy-switch-macro-recording` function from [handy-mode](https://github.com/superhandy/handy-mode) for Emacs)
* `Alt+M, L`: Runs the last recorded macro (e.g. `kmacro-end-and-call-macro` on Emacs)
* `Alt+M, J`: Edit (and then Save) a macro (e.g. `handy-switch-macro-editing` function from [handy-mode](https://github.com/superhandy/handy-mode) for Emacs)

Commands about bookmarks:

* `Alt+M, I`: `bookmark-jump`
* `Alt+M, K`: `bookmark-set`
* `Alt+M, B`: `bookmark-bmenu-list`

Commands about registers:

* `Alt+M, Alt+I`: `jump-to-register`
* `Alt+M, Alt+K`: `point-to-register`
* `Alt+M, Alt+C`: `copy-to-register`
* `Alt+M, Alt+V`: `insert-register`

### Level 3 UO

          .-----.-----.-----.
          |  U  |     |  O  |
          |-----'     '-----|
          |                 |
    .-----'-----------------'
    |           |
    '-----------'

* `Alt+U`: `backward-word`
* `Alt+O`: `forward-word`
* `Alt+Shift+U`: `handy-beginning-of-block`
* `Alt+Shift+O`: `handy-end-of-block`

### Level 4 ZB

                                        .-----.-----.-----.
                                        |     |     |     |
                                        |-----'     '-----|
                                        |                 |
    .-----------------------------.-----'-----------------'
    |  Z     X     C     V     B  |           |
    '-----------.                 '-----------|
                |             SPC             |
                '-----------------------------'

...

### Level 5 YH

                                  .-----.-----.-----.-----.
                                  |  Y  |     |     |     |
                                  |     |-----'     '-----|
                                  |  H  |                 |
    .-----------------------------|-----'-----------------'
    |                             |           |
    '-----------.                 '-----------|
                |                             |
                '-----------------------------'

...

* `Alt+Y`/`Alt+Shift+Y`: Forward/backward incremental search (e.g. `isearch-forward`/`isearch-backward` on Emacs)
* `Alt+H`/`Alt+Shift+H`: If you press one time the key it goes to the
  beginning/end of line (e.g. `Alt+H` goes to the beginning of line),
  the second time you press it, it goes to the beginning/end of file
  (e.g. `Alt+H, Alt+H` goes to the beginning of file)
  (`handy-beginning-of-line-and-buffer`/`handy-end-of-line-and-buffer`)

### Level 6 WERD

          .-----------------.     .-----.-----.-----.-----.
          |  W     E     R  |     |     |     |     |     |
          '-----.           '-----|     |-----'     '-----|
                |  D     F     G  |     |                 |
    .-----------'-----------------|-----'-----------------'
    |                             |           |
    '-----------.                 '-----------|
                |                             |
                '-----------------------------'

...

* `Alt+W`: `handy-shrink-whitespace`
* `Alt+E`: `backward-kill-word`
* `Alt+R`: `kill-word`
* `Alt+D`: `delete-backward-char`
* `Alt+F`: `delete-char`
* `Alt+G`: `kill-char`

* `Alt+Shift+W`: `handy-close-file`
* `Alt+Shift+D`: `backward-kill-sexp`
* `Alt+Shift+F`: `kill-sexp`
* `Alt+Shift+G`: `handy-backward-kill-line`

### Level 7 Modal

Using `Alt+Enter` you can lock the `Alt` key prefix for all other
levels, so the first `Alt` is not necessary to be pressed. Pressing
`Alt+Enter` disable the lock and you are back to the normal editing
mode (where `Alt` modifier is required to execute the regular commands
in all other levels).

* The bad thing about this is that you cannot write text on this mode
  (e.g. pressing `L` key means `Alt+L` instead of writting the key `L`).
* The god side is that you can move easily in the file without
  pressing the `Alt` modifier all the time.

The idea of `Alt+Enter` is that depending on what you need to do you
can lock the `Alt` key (for navigation) or unlocked (for editing).

## Text Editors

How to configure each text editor?

* For bash/readline: [.inputrc](https://github.com/superhandy/inputrc) file
* For zshrc: [.zshrc](https://github.com/superhandy/zshrc) file
* For Emacs: [handy-mode](https://github.com/superhandy/handy-mode)

## Acknowledges

`handy` is based on ideas from:

* [Xah Lee's ideas about Emacs](http://ergoemacs.org/emacs/emacs_keybinding_redesign.html),
* [ErgoEmacs](http://ergoemacs.org/) and [ErgoEmacs keybinding](http://ergoemacs.org/emacs/ergonomic_emacs_keybinding.html), and
* [dacap's ergoprog mode](https://github.com/dacap/ergoprog).
* [Incomplete experimental handy text editor](https://github.com/dacap/handy).
