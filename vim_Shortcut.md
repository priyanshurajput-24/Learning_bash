# Vim Commands

## Syntax Highlighting
- `:Syntax on` : Enable syntax highlighting.
- `:set nu` : Show line numbers.
- `:colorscheme` (press `Ctrl + d`) : Show color schemes.
- `:colo <color-scheme-name>` : Try out color schemes.
- `:<Any Line Number>` in insert mode : Go to a specific line number.
- `:$` : Move the cursor to the end of the current line.
- `:0` : Move the cursor to the start of the current line.
- `:dw` : Delete the letter after the cursor before the next word.
- `:dd` : Delete the entire line.
- `:undo` or type `<u>` : Undo the last change.
- `:redo` or type `<Ctrl-r>` : Redo the last change.
- `:<line number>` : Take the cursor to the specified line number.
- `Ctrl+f` : Scroll down by one full screen.
- `Ctrl+b` : Scroll up by one full screen.
- `:split <file name>` or `:sp <file name>` : Split the same window horizontally. Switch between splits via `Ctrl + ww`.
- `:vs <file name>` : Vertically split the window.
- `w` in `ex` mode : move the pointer to next word.
- `b` in `ex` mode : move the pointer to previous word.
- `(Press Ctrl + e)` : move the pointer one line up(next line) 
- `(Press Ctrl + y)` : move the pointer one line down(previous line)

## Visual Block Mode
1. Press `Ctrl+V` to enter visual block mode.
2. Move the cursor to the end of the selection.
3. Press `y` to copy or `d` to cut.
4. Move the cursor to the paste location.
5. Press `P` (uppercase) to paste before the cursor.

## Selection Commands
- To select the entire file: `ggVG` (Explanation: gg moves to the first line, V enters Visual Line mode, and Shift+g moves to the last line).

## Vi Related Commands
1. Copy a file into the current file: `:r <path to file>`
2. Open a new buffer: `:enew` (Save file before moving to the next buffer).
3. Go to the next buffer: `:bn`
4. Go to the previous buffer: `:bp`
5. Delete the buffer: `:bd`
6. Edit a file in the current buffer: `:e <file name>`

## Visual Mode Commands
- Enter visual mode: `v`
- Select lines, copy with `y`, paste with `p`.
