### VIMTUTOR

[https://github.com/ninja-janin/vimcheat](https://github.com/ninja-janin/vimcheat)
[https://gist.github.com/tuxfight3r/0dca25825d9f2608714b](https://gist.github.com/tuxfight3r/0dca25825d9f2608714b)

### VIM TUTOR ON ATOM EDITOR
[https://github.com/t9md/atom-vim-mode-plus/wiki/AdvancedTopicTutorial](https://github.com/t9md/atom-vim-mode-plus/wiki/AdvancedTopicTutorial)


### NERDTREE
```sh
Open v
N + back slash - opening nerdtree
:NERDTree
s - horizontal split
i - vertical split

R - refresh / reload nerdtree
I  - to toggle hidden files
m - type a after to add new file
m - type a then write the filename then append '/' to create directory
m - type m to rename the file

Ctrl + b + fn + arrow up - make scrollable in terminal
s - for new tab column
```

### MOVING CURSOR
```sh
h - left
j - down
k - up
l - right
```

### TRANSFERRING TO EACH TAB
```sh
Ctrl + b + h  | j | k | l - arrow keys
```

### TMUX
```sh
Create split tab
Ctrl + b + %
Create new tab

Ctrl + b + c

Transferring to each tab
Ctrl + b + 1 | 2 | 3 and so on
```

### COMMANDS
```sh
ESC - NORMAL mode
i - INSERT mode
v - VISUAL mode

x - remove letter starting from the right
a | A - to append texts after the line

u - undo changes
U - undo changes of the current line
cmd + r - undo the undos
. - redo
ctrl + R - redo

R - replace characters
rx - replace the character where x is the character

o - add new line below cursor and change to INSERT mode
O - add new line above cursor and change to INSERT mode

~ - swap letter case
g~ - switch case under cursor
V~ | g~~ | gUU | guu- swap case of the line
```

### MOVEMENT
```sh
b - to move back to the beginning of the word
e - to move to the next incomplete word and repeat
j - to move the cursor to the end of next line
^ - to move to the first character of the line

ctrl + g - controls your location in the file
gg - go to top line
G - go to bottom line
{number} + g | h | j | k | l - go to specific line

<< - move lines to left
>> - move line to right
```

### DELETION
```sh
d - delete operator (d+{MOTION})
MOTION - is what the operator will operate on
dw - to delete a word
d$ - to delete to the end of the line
de - delete the end of the current word, INCLUDING the last character

COUNT TO DELETE
d2w - deleting two UPPER CASE words where 2 is the count
dd - delete the line
2dd - deleting two lines where 2 is the count
```

### DELETE THEN INSERT MODE
```sh
c - delete operator (c+{MOTION}) same with d motion
cw - delete a word
c$ - delete words of a line after the cursor
ce - remove the words after the cursor to the end of the word

COUNT TO DELETE
c2w - deleting two UPPER CASE words where 2 is the count
cc - delete the line
2cc - deleting two lines where 2 is the count
```

### SAVING AND EXIT
```sh
:q - exits file
:q! - exits the editor, discarding any changes you have made
:wq - to save a file and exit
:w - save a file without exit
```

### COUNT MOTION
```sh
0 - back to the first line
2w - move the cursor two words forward
3e - move the cursor to the end of the 3rd word of the line INCLUDING last character of the 3rd word
```

### SEARCHING
```sh
/: -
/ - search for phrase + CTRL+0 to search for same character
? - search for phrase backward direction
n - next to searched phrase, N - opposite direction
CTRL-O takes you back to newer positions, CTRL-I to newer positions

% - move cursor to the start of matching parenthesis or bracket
:%s/new/new/g - to change every occurrence in the whole file
Example: Search New then change to new

:%s/new/new/gc - to change every occurrence in the whole file with a promp
:s/new/new - to substitute new for the first new in a line type
:s/new/new/g - to substitute new for all 'new's on a line type
:#,#s/new/new/g - to substitute phrases between two line #'s type

Typing ":set xxx" sets the option "xxx".  Some options are:
'ic' 'ignorecase' - ignore upper/lower case when searching
'is' 'incsearch'  - show partial matches for a search phrase
'hls' 'hlsearch'  - highlight all matching phrasesa
:set hls is - highlight searched phrase
/ignore\c - highlight ignore word for once
:nohlsearch - ignore highlighted phrases
:set noic - not include case

Example:
search /ignore
type :set noic - not include texts with uppercase case letters
```

### HIGHLIGHTING
```sh
v - highlight character
V - highlight the whole line
plus h | j | k | l arrow keys to highlight down or up texts

press : and it will show you :<','>
type w TEST where TEST is the filename that does not exist yet
use :!dir or :!ls to check if there are changes

:r TEST - retrieves the contents on this file
:r !ls - retrieves the ls command and puts it below the cursor

:!command  executes an external command.

Some useful examples are:
(MS-DOS)         (Unix)
:!dir            :!ls            -  shows a directory listing.
:!del FILENAME   :!rm FILENAME   -  removes file FILENAME.
```

### COPY AND PASTE FROM EXTERNAL
```sh
:w !pbcopy - copy clipboard from outside
cmd + v - paste
```

### WRAP LINES
```sh
:set wrap linebreak
```

### YANK AND PUT INSIDE VIM
```sh
yyp - copy and paste lines
y - copy
yw - yanks one word
p - paste
:%y - copy all lines
```

### FOR BEAUTIFIER
```sh
npm -g install js-beautify
:%!js-beautify
```

### BUFFERS
```sh
:ls - list available buffers
```
