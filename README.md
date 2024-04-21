# learn_vim
The most important information:

[How to exit vim](#exit-vim)

[How to pair with vim](#how-to-exit-vim)

The following should work for neovim, vim, vi, and vim plugins for other editors too. But I'll use vim to refer to all of them.

## Getting started

The easiest option is to add vim mode to whatever editor or IDE you're currently using.
That way you learn vim at your own pace, and are less likely to get overwhelmed: eg, 
[vscodevim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim) or
[IdeaVim](https://www.jetbrains.com/help/idea/using-product-as-the-vim-editor.html).

If you want to dive into the deep end and try it as your main editor, follow these steps to setup neovim:
[nvim-lua/kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim)

## Modes

Other editors default to entering text. This makes sense at first, surely the most important thing is typing text in an editor?

But in vim, you default to giving the editor actions, then switch modes to enter text. The idea is that *editing* text is the more important part. You *edit* text by naviating around a document and modifying the existing text.

So for example in vscode to modify the next two words, you might:

- hold SHIFT + hold OPTION + press right arrow twice to select 2 words
- then type the replacement text, overwriting the selected text

Instead of thinking of the first step as a key combination, you can think of each modifier key you hold down as temporarily switching to a different mode.
- SHIFT changes to selecting text mode.
- OPTION changes arrows to move by words rather than characters.
- Once you release these modifier keys, you're back to entering text.

In vim you're always in a specific mode, and you explicitly switch between them.
In vim to modify the next two words, you might:

- type `c2w`
- then type the replacement text
- then press ESC to switch back to Normal mode

The `c` part switches modes, so you can type out the replacement text.
The `2w` part indicates what text you want to modify.
As you type out the above, vim waits until you've finished typing a whole command, then executes it all at once.
It has a specific grammar for actions, so it doesn't need to wait a specified amount of time or for an ENTER.

Vim has various modes, with each mode being used for different kinds of tasks.

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

Actions in normal mode are typed out normally and do not require ENTER to run.

In other editors, you hold down combinations of Control,Shirt,Option, Command, and other keys to do these actions.

From other modes:

`ESC` to get back to Normal mode.


### Insert
Used for actually typing text.

From Normal mode:

`i` to switch to Insert mode.

### Command
Used for giving the editor commands.
Things like saving, quiting, opening files or enabling options.

It shows a `:` in the bottom left, and you type out the command then press ENTER to run it.

In other editors, you often use a menu, or a command palette with Control+Shift+p to run these commands.

From Normal mode:

`:` to switch to Command mode.

#### Search
Used for searching for text using regex.
It's a form of Command mode that will show a "/" in the bottom left and say "Command" above that.

`/` to switch to Search mode.

Then type the text you want to search for, and press ENTER.
then use `n` to find the next match, or `N` to find the previous match.

### Visual
Used for selecting text.
This allows you to use the same keys as Normal mode.

In other editors, you use the mouse to drag and select things, or hold down shift as you select the text.

From Normal mode:

`v` to switch to visual mode by character.

## The vim language

The power of Normal mode is that actions are built using a basic grammar.

<optional verb><optional modifier><motion>

eg `w` means move to the start of the next word.
eg `2w` means move 2 words.
eg `d2w` means <delete><two><words>.

So as you learn more verbs and motions you can combine them with the ones you already know.

Verbs are things like `d` for delete, `y` for yank (copy), `c` for change, `u` for undo, `CTL+r` for replace.

Motions are things like `w` for word, `s` for sentence, `l` for line. Or `fp` for find the next "p" character.
Motions can include modifiers, like numbers multiply the motions, or contextual like `a` for around

Motions can also be used without a verb, to just move around.

### Motions and navigation

Just moving around vim can be confusing at first.

`h j k l` are the arrow keys, left, down, up, right. Which is pretty strange, but they're right on the home row.

There's all kinds of other ways to move around.

`$` to move to the end of the line.

`0` to move to the start of the line.

`^` to move to the first non-whitespace character of the line.

`{ }` to move to the start of the previous/next paragraph.

`w b` to move by forwards and backwards by a word, defined by punctuation.

`W B` to move by word, defined by spaces.

`%` to move to the matching bracket/braces/parens.



## More ways to switch modes

When there are multiple options, they are separated with a space.
eg `i o` means either "i" or "o"

```mermaid
flowchart TD
    Insert -- "&nbsp; ESC &nbsp;" --> Normal
    Normal -- "&nbsp; i I A o O C &nbsp;" --> Insert
    Normal -- "&nbsp; : &nbsp;" --> Command
    Normal -- "&nbsp; v &nbsp;" --> VisualCharacter
    Normal -- "&nbsp; V &nbsp;" --> VisualLine
    Normal -- "&nbsp; CTRL+v &nbsp;" --> VisualBlock
    VisualCharacter -- "&nbsp; ESC &nbsp;" --> Normal
    VisualLine -- "&nbsp; ESC &nbsp;" --> Normal
    VisualBlock -- "&nbsp; ESC &nbsp;" --> Normal
    Command -- "&nbsp; qa! &nbsp;" --> ExitVim
```

### More ways to Insert

`i` to enter text before the cursor.

`I` to enter text at the start of the line.

`A` to enter text at the end of the line.

`o` to enter text in a new line below.

`O` to enter text in a new line above.

`C` to change the rest of the line



### Visual line and block
Visual mode is by character, but it can also be by whole lines, or a block.

From Normal mode:

`v` to switch to visual mode by character.

`V` (`SHIFT+v`) to switch to line visual mode.

`CTRL+v` to switch to block visual mode.

### Special Modes
You'll probably want to avoid these.

#### Command Line Window

Used to edit your history of commands, allowing you to use Normal mode keys to navigate and edit the commands.

It will show a colon ":" and say "Normal".

`CTRL+c` to exit this mode. Then press ESC to get back to Normal mode.

#### Ex
Emulates the very old "ed" editor.

It will show a colon ":", but ESC doesn't work.

`:q` you'll see a colon, type q then press ENTER, to exit this mode.

## Links
[ Vim Survival Guide ]( https://www.fusionbox.com/blog/detail/vim-survival-guide/609/ )

[Learning Vim in 2014: Vim as Language](https://benmccormick.org/2014/07/02/062700.html)

## vim tutor
in vim press Escape, then type:
`:Tutor`

## How to pair with vim
Some basic commands to get by when pairing with someone who uses vim.
Ask them to enable the arrow keys, so you can do basic navigation,
Ask them to enable the mouse, so you can scroll and click around.
And ask them to enable the operating system clipboard, so you can copy and paste.

When in Normal mode:

`i` then start typing

`ESC` back to normal mode

`u` undo

`CTRL+r` redo

`:w` save

`:e filename` to edit a file


## Exit vim
Quiting vim can be the most confusing part to start with.

Vim has multiple modes, so depending on which mode you're in you might need to try a few options to exit.

`ESC` press the Escape key. At the bottom left it should say "Normal".

`:` press the colon key. You should see a colon in the bottom left. It should say "Command" just above the ":".

`qa!` type "qa!" then press ENTER. This will quit all windows without saving.

If none of that works, try:

`CTRL+c` If you see the colon, and it also says "Normal".

`CTRL+z` if you're really stuck you can suspend vim and go back to the terminal.
