# Command redirection

Every linux command or program we run has three data streams connected to it.
1. STDIN (0) --> Standard Input
2. STDOUT (1) --> Standard Output
3. STDERR (2) --> Standard Error

## Output Redirection
To redirect the output of a command to a file we can use the greater than ```>``` symbol. For exampe: ```ls -la > uotput.txt```. When we use this command, few things happen:
- If the file is not created, it will create the file
- If the file content exist, it will be overwritten
- The output will not be shown in the terminal

To avoid getting overriten wecan use double greater than ```>>``` command. If we use the same command with this for example ```ls -la >> uotput.txt```, this time it will not override the file content.

## Error redirection
STDERR has the stream number 2. We can use it to redirect error messages produced by a command to an error file. For example: ```ls /home /nonexistent 2> errors.txt``` in this command, the ls will try to list the both specified directorie, the /home directory list output will be shown at the terminal and the error message will be saved at error.txt

## Piping
The pipe ```|``` takes the output of the previous command and passess to the next command. For example: ```cat file.txt | grep password | tee output.txt``` . In this example, the piping takes the input of cat command and passes it to the grep, then output of grep command again passed to the tee command. Finally the tee command shows the output in terminal and saves it to output.txt.

The redirect (```>```) does not show the output in terminal but the tee command does. 

## Word count (wc)
To count the available number of lines, words, files use the command `wc file` Then we can use options: `-l` to show the line numbers, `-c` to the number of characters, and `-w` to show number of wards available on that file.

