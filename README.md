# learn_vim
Resources for learning vi/vim/neovim editors and vim modes in other editors.

## Exit vim
Quiting vim can be the most confusing part to start with.

Vim has multiple modes, so depending on which mode you're in you might need to try a few options to exit.

`ESC` press the Escape key. At the bottom left it should say "Normal".

`:` press the colon key. You should see a colon in the bottom left. It should say "Command" just above the ":".

`qa!` type "qa!" then press Enter. This will quit all windows without saving.

If none of that works, try:

`CTRL+c` If you see the colon, and it also says "Normal".

`CTRL+z` if you're really stuck you can suspend vim and go back to the terminal.

## Key
`CTRL+c` means hold down the Control key and press c.

`SHIFT+c` means hold down the Shift key and press c, same as typing a capital C.

`ESC` means press is the escape key.

`ENTER` means press the Enter key.

`yaw` means press y, then a, then w.

## Modes

Other editors default to entering text. Then you hold down modifier keys to temporarily perform other actions.

But in vim, you default to giving the editor actions, then switch modes to enter text.

So for example in vscode, to copy 2 words, you might:

- hold SHIFT to select
- hold ALT to move by word
- press right arrow twice to select 2 words
- then hold CMD then press "c" to copy

In vim, you might:

- type `y2w` to yank (copy) 2 words

Vim has various modes, with each mode being used for different kinds of tasks.

Note: You won't get much feedback from different actions, vim will just do what you tell it to.


### Basics for switching mode

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

Normal mode is your home base, and you'll go into other modes from there.

In other editors, you hold down combinations of Control,Shirt,Alt, and Super/Command/Windows keys to do these actions.

From other modes:

`ESC` to get back to Normal mode.


### Insert
Used for actually typing text.

From Normal mode:

`i` to enter Insert mode.

### Command
Used for giving the editor commands.
Things like saving, quiting, opening files or enabling options.

It shows a `:` in the bottom left, and you type out the command then press Enter to run it.

In other editors, you often use a menu, or a command palette with Control+Shift+p to run these commands.

From Normal mode:

`:` to enter Command mode.

### Visual
Used for selecting text.
This allows you to use the same keys as Normal mode.

In other editors, you use the mouse to drag and select things, or hold down shift as you select the text.

From Normal mode:

`v` to enter visual mode by character.


### More advanced mode switching

When there are multiple options, they are separated with a space.
eg `i a o` means either "i" or "a" or "o"

```mermaid
flowchart TD
    Insert -- "&nbsp; ESC &nbsp;" --> Normal
    Normal -- "&nbsp; i I a A o O &nbsp;" --> Insert
    Normal -- "&nbsp; : &nbsp;" --> Command
    Normal -- "&nbsp; v &nbsp;" --> VisualCharacter
    Normal -- "&nbsp; V &nbsp;" --> VisualLine
    Normal -- "&nbsp; CTRL+v &nbsp;" --> VisualBlock
    VisualCharacter -- "&nbsp; ESC &nbsp;" --> Normal
    VisualLine -- "&nbsp; ESC &nbsp;" --> Normal
    VisualBlock -- "&nbsp; ESC &nbsp;" --> Normal
    Command -- "&nbsp; qa! &nbsp;" --> ExitVim
```

#### Visual line and block
Visual mode is by character, but it can also be by whole lines, or a block.

From Normal mode:

`v` to enter visual mode by character.

`V` (`SHIFT+v`) to enter line visual mode.

`CTRL+v` to enter block visual mode.

### Special Modes
You'll probably want to avoid these.

#### Command Line Window

Used to edit your history of commands, allowing you to use Normal mode keys to navigate and edit the commands.

It will show a colon ":" and say "Normal".

`CTRL+c` to exit this mode. Then press ESC to get back to Normal mode.

#### Ex
Emulates the very old "ed" editor.

It will show a colon ":", but ESC doesn't work.

`:q` you'll see a colon, type q then press Enter, to exit this mode.

## Links
https://www.fusionbox.com/blog/detail/vim-survival-guide/609/

## vim tutor
in vim press Escape, then type:
`:Tutor`
