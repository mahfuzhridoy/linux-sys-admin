# Man page
Man page is short form of manuals. usermanual of commands live here. When someone needs to know about the usage of a command they can simply add prefix man to the command. for example:
```man ls```. this will show the manual page of ls command in terminal.
 
We can type h inside the man page to see the further help menu about terminal shortcuts and how to navigate through the man page.

press ```q``` to exit from the help menu then press q again to exit from man page

## Man page description

#### NAME
The first line of the page under NAME section contains the name of the command and very short description.

#### SYNOPSIS
The second line SYNOPSIS provide a simple structure of command line. Everything that appears in front of 3 dors also called elipses can be repeated many times. For example: ```ls [OPTION]... [FILE]...``` here the **[option]** and **[file]** appeared before 3 dots, so they can be repeated.

**[Note: Options and argument are put between square brackets to tell that they can be leftout. They are not necessary here in this command.]**

#### DESCRIPTION
If the texts are in bolds like **```this```**, It must be typed as it is seen. But, when the text is underlined or in *Italic* the text must be replaced with something else. for example: --block-size=*SIZE*, here the SIZE must be replaced with something appropriate. 

At the bottom there are AUTHOR, COPYRIGHT, and SEE ALSO section.

## Important navigation

#### Up and Down
To move line up and down press the arrow up or arrow down keys
### Forward One Window
Press: ```ctrl + f or space``` to forward one window. To move backwards press: ```ctrl + b```

#### Go to Very beggining and end
type lowercase ```g``` to go the starting of man page and press uppercase ```G``` to go to the end of the man page

#### Searching
Sometimes searching for the specific options. we can do that by pressing an back slash ```/``` in the man page then type the desired word and press enter. the search term will be highlighted. Now pressing ```n``` will take to the next matched search term and uppercase ```N``` to previous one

# Command types

There are 2 types of commands:

1. executable file commands
2. shell built in commands

executable file commands are saved inside the ```/usr/bin``` directory. To find out if the command is executeable or shell built in use ```type``` command. For example: ```type apt``` it will display the path to the command. But commands like cd, alias, unmask are shell built in. they dont have dedicated man page. 

### help for shell built in commands
```help``` commands can be only used for shell built in commands. they are not for executable commands. To do so type ```help unmask``` and a help menu will appear. 


### -h, --help option for all
This option is available for both shell and executive command.

# Search in all Man page **
to search in all man pages about the desired command ```man -k [command]``` will find the commands. it can be also written like ```man -k "copy files"``` and it will search for the provided string in all man pages.
 another option is ```apropos [command]``` to do so.

Now a user can move deeper with man commands.