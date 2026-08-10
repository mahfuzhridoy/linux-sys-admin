# Comparing File Contents

### cmp command

cmp Compares the files byte by byte and displays the location of first mismatch. It doesn't say how the file differs and if the files are identical, no message is displayed. For example: ```cmp file1.txt file2.txt```. 

This command can be also used to compare binary files. for example: ```cmp /usr/bin/ls /usr/bi/ls``` these two are binary files and we can compare it. However they are identical here so no message will be shown.

### Sha256

Another way to compare the binary file is to calculate and compare their hash. hash is a cryptographic term. We can do it with ```sha256sum /usr/bin/ls /usr/bi/ls```. If a single bit is different, the hash value will be different.

**[Note: This technique can be used to find out the authenticity of a software or file to identify that we have downloade a correct file/software which has not been changed by someone for malicious intent]**

### diff command

diff command is only used for text files. For example: ```diff a b```. It shows where the file differs line by line.

The diff command helps us to make the file identical. It also helps us patch files. we can do the using the ```patch``` tool. Some more useful options:
- ```-B``` Ignore blank lines
- ```-w``` to ignore white spaces
- ```-i``` to ignore case differences
- ```-c``` for more detailed comparisond
- ```-y``` for side by side comparison in two columns

