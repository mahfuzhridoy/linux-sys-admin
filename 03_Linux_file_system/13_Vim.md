# Vim text editor
Vim is a modal text editor. It is most used text editor by the system administrator in the world. There are few other command line text editors too like `nano`. But vim has more functionality than nano.

#### Some basic modes of vim are:

- command
- insert
- last line


### Command mode
While a file is opened,  It is normally inside command mode. When typing in a command mode, out actions will work as commands. For example: pressing `x` will delete the character under the cursor. Or, `r` will enter replace mode tht will replase the character under the cursor as typed. 

### Insert mode

To return to command mode from other modes press `esc` one or more times. To start writing, We need to enter insert mode by pressing `i` then we can write as we want. 

[Note: Always be cautious about which mode you are in]

Pressing uppercase `I` starts entering texts at the beginning of the line. Pressing `a` jumps to append mode that will append characters in the cursor place. Uppercase `A` will append the characters of the current line.

Lower case `o` will start entering text below the current cursor line. And uppercase `O` to write above the current line.

### Last line mode
To go to last line mode from command mode press `:` key. After pressing you will see a colon at the last line. From last line we can do the actions like Quiting, saving, quit without saving, save and quit etc. Their commands:

first go to last line mode by pressing `:` then

- `q!` and press `enter` quit without saving
- `w!` and then `enter` saves the file without quiting
- `wq!` then `enter` save and quit.
- `shift` + `zz` save ad quit shortcut. does not require to enter last line mode.
- `set nu` to display the line numbers. `set nonu` for no number
- `syntax on` to enable syntax coloring and `syntax off` for disable syntax coloring.
- `100` to move line 100
- `G` to end of the file and `gg` or `1` to the beginning.

#
- comparing file side by side `vim -o file1 file2`. move between windows by `ctrl + w` useful for copy pasting from one file to another.

- Find differences `vim -d file1 file2` will highlight the differences.  move between windows by `ctrl + w`. Another option is `vimdiff file1 file2`
#

If not exited properly with command, it will give a prompt to the user, Press `r` to recover the file.

To learn and practice vim, run  `vimtutor` on the terminal. It will not change the file content. It is only for practce. To permanently chage vim configuration change `~/.vimrc` file. 



# Deep dive into vim
We can run shell command when we are inside a vim text editor file. For example: Go to the vim last line mode and then:

[Note: to execute the commands in last line mode enter is need to be pressed]

- `!ls` Will run the ls command
- `!ifconfig` will run the command
- `/search text` will search for matched string. Then navigate between matches with `n` and `N` for forward and backward navigation.
- capital `G` will take to the end of the file.
- `?search term` for reverse term search from the end of the file.
- `*` to find the same word under the cursor appeared next time
- `#` to finde the same word under the cursor appeard previously.

- Replacing all occurences of a character in the last line mode, `%s/no/yes/g` will replace all occurences of no with yes
- Undo in the last line mode to go back to last saved version in command lin mode `e!`.
- Undo the last operation, go to command mode not last line mode then press `u`, this is equivalent to `ctrl + z` in graphical text editor.
- To redo press `ctrl + r`.

#### Cutting, copying and pasting a line

- cut a line press `dd`
- to paste in the cursor place press `p`.

#### cutting more then one line 
- type the number then type `dd`. For example: `10dd` will cut 10 lines. then `p` to paste.

#### copying text

Firs step is to position the cursor where we want to begin. Then `shift + v` to select the line, `v` to select characters, `ctrl + v` to select ewctangular blocks.

For example: Press `Shift + v` then use the arrow up and down keys to continue selecting lines.

Once selection is done press `y` to copy the selections. Then obviously, capital `P` to paste before the cursor and `p` to after the cursor.


