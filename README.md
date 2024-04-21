# learn_vim
Resources for learning vim

## Exit vim
Vim has multiple modes, so depending on which mode you're in you might need to try a few options to exit.
So this can be the most confusing part of vim to start with.

`ESC` press the Escape key. At the bottom left it should say "Normal".

`:` press the colon key. You should see a colon in the bottom left. It should say "Command" just above the ":".

`qa!` type "qa!" then press Enter. This will quit all windows without saving.

If none of that works, try:

`C-c` If you see the colon, and it also says "Normal".

`C-z` if you're really stuck you can suspend vim and go back to the terminal.

## Key
`C-c` means hold down the Control key and press c. This can also be written `<C-c>`.

`S-c` means hold down the Shift key and press c, same as typing a capital C. This can also be written `<S-c>`.

`ESC` means press is the escape key.

`CR` means press the Enter key, (Carriage Return).

`yaw` means press y, then a, then w.

## Modes

Vim has various modes, with each mode being used for different tasks.

Note: You won't get much feedback from different actions, vim will just do what you tell it to.

### Basics for changing mode

```mermaid
flowchart TD
    Insert -- "&nbsp;ESC&nbsp;" --> Normal
    Normal -- "&nbsp;i&nbsp;" --> Insert
    Normal -- "&nbsp;:&nbsp;" --> Command
    Normal -- "&nbsp;v&nbsp;" --> Visual
    Visual -- "&nbsp;ESC&nbsp;" --> Normal
    Command -- "&nbsp;qa!&nbsp;" --> ExitVim
```

### Normal
Used for navigation and editing text. You can't actually type text in this mode, which will seem strange at first. But for coding, this is actually the most useful mode. That's why it's called normal mode.

In other editors, you hold down combinations of Control,Shirt,Alt, and Super/Command/Windows keys to do these actions.

From other modes:

`ESC` to enter Normal mode.


### Insert
Used for actually typing text.

From Normal mode:

`i` to enter Insert mode.

### Command
Used for giving the editor commands.
Things like saving, quiting, opening files or enabling options.

It shows a `:` in the bottom left, and you type out the command then press Enter to run it.

In other editors, you often use a menu, or a command palette with Control+Shift+p (C-S-p) to run these commands.

From Normal mode:

`:` to enter Command mode.

### Visual
Used for selecting text.
This allows you to use the same keys as Normal mode.
This can be by character, whole lines, or a block.

In other editors, you use the mouse to drag and select things, or hold down shift as you select the text.

From Normal mode:

`v` to enter visual mode by character.


### More advanced mode changes

When there are multiple options, they are separated with a space.
eg `i a o` means either i, a, or o.

```mermaid
flowchart TD
    Insert -- "&nbsp;ESC&nbsp;" --> Normal
    Normal -- "&nbsp;i a o&nbsp;" --> Insert
    Normal -- "&nbsp;:&nbsp;" --> Command
    Normal -- "&nbsp;v V C-v&nbsp;" --> Visual
    Visual -- "&nbsp;ESC&nbsp;" --> Normal
    Command -- "&nbsp;qa!&nbsp;" --> ExitVim
    Command -- "C-f" --> CommandLineWindow
    CommandLineWindow -- "C-c" --> Command
```

### Special Modes
You'll probably want to avoid these.

#### Command Line Window

Used to edit your history of commands, allowing you to use Normal mode keys to navigate and edit the commands.

`C-c` Control+c to exit this mode.

#### Ex
Emulates the very old "ed" editor.

`:q` type q then press Enter, to exit this mode.

## Links
https://www.fusionbox.com/blog/detail/vim-survival-guide/609/

## vim tutor
in vim press Escape, then type:
`:Tutor`
